---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-list?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-List
ms.openlocfilehash: c0d5c5b9ed6beed635b9df1ba9523b29c5cac9eb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205062"
---
# Update-List

## SYNOPSIS
Ajoute et supprime des éléments dans une valeur de propriété qui contient une collection d'objets.

## SYNTAX

### AddRemoveSet (par défaut)

```
Update-List [-Add <Object[]>] [-Remove <Object[]>] [-InputObject <PSObject>] [[-Property] <String>]
 [<CommonParameters>]
```

### ReplaceSet

```
Update-List -Replace <Object[]> [-InputObject <PSObject>] [[-Property] <String>] [<CommonParameters>]
```

## Description

L' `Update-List` applet de commande ajoute, supprime ou remplace des éléments dans une valeur de propriété d’un objet et retourne l’objet mis à jour. Cette applet de commande est conçue pour les propriétés qui contiennent des collections d'objets.

Les paramètres **Add** et **Remove** ajoutent et suppriment des éléments individuels dans la collection.
Le paramètre **Replace** remplace l’intégralité de la collection.

Si vous ne spécifiez pas de propriété dans la commande, `Update-List` retourne un objet qui décrit la mise à jour au lieu de mettre à jour l’objet. Vous pouvez envoyer l’objet de mise à jour à des applets de commande qui modifient des objets, tels que des `Set` applets de commande.

Cette applet de commande fonctionne uniquement lorsque la propriété en cours de mise à jour prend en charge l’interface **IList** utilisée par `Update-List` . En outre, toutes les `Set` applets de commande acceptant une mise à jour doivent prendre en charge l’interface **IList** .

Les applets de commande de base qui sont installées avec PowerShell ne prennent pas en charge cette interface. Pour déterminer si une applet de commande prend en charge `Update-List` , consultez la rubrique d’aide sur l’applet de commande.

Cette applet de commande a été réintroduite dans PowerShell 7.

## EXEMPLES

### Exemple 1 : ajouter des éléments à une valeur de propriété

Dans cet exemple, nous créons une classe qui représente un jeu de cartes où les cartes sont stockées sous la forme d’un objet de collection de **listes** . La méthode **NewDeck ()** utilise `Update-List` pour ajouter un jeu complet de valeurs de carte à la collection de **cartes** .

```powershell
class Cards {

    [System.Collections.Generic.List[string]]$cards
    [string]$name

    Cards([string]$_name) {
        $this.name = $_name
        $this.cards = [System.Collections.Generic.List[string]]::new()
    }

    NewDeck() {
        $_suits = "`u{2663}","`u{2666}","`u{2665}","`u{2660}"
        $_values = 'A',2,3,4,5,6,7,8,9,10,'J','Q','K'
        $_deck = foreach ($s in $_suits){ foreach ($v in $_values){ "$v$s"} }
        $this | Update-List -Property cards -Add $_deck | Out-Null
    }

    Show() {
        Write-Host
        Write-Host $this.name ": " $this.cards[0..12]
        if ($this.cards.count -gt 13) {
            Write-Host (' ' * ($this.name.length+3)) $this.cards[13..25]
        }
        if ($this.cards.count -gt 26) {
            Write-Host (' ' * ($this.name.length+3)) $this.cards[26..38]
        }
        if ($this.cards.count -gt 39) {
            Write-Host (' ' * ($this.name.length+3)) $this.cards[39..51]
        }
    }

    Shuffle() { $this.cards = Get-Random -InputObject $this.cards -Count 52 }

    Sort() { $this.cards.Sort() }
}
```

> [!NOTE]
> L' `Update-List` applet de commande génère l’objet mis à jour dans le pipeline. Nous allons diriger la sortie vers `Out-Null` pour supprimer l’affichage indésirable.

### Exemple 2 : ajouter et supprimer des éléments d’une propriété de collection

Si vous continuez avec le code de l’exemple 1, nous allons créer des instances de la classe **Cards** pour représenter un jeu de cartes et les cartes détenues par deux joueurs. Nous utilisons l' `Update-List` applet de commande pour ajouter des cartes aux mains des joueurs et pour supprimer des cartes du jeu.

```powershell
$player1 = [Cards]::new('Player 1')
$player2 = [Cards]::new('Player 2')

$deck = [Cards]::new('Deck')
$deck.NewDeck()
$deck.Shuffle()
$deck.Show()

# Deal two hands
$player1 | Update-List -Property cards -Add $deck.cards[0,2,4,6,8] | Out-Null
$player2 | Update-List -Property cards -Add $deck.cards[1,3,5,7,9] | Out-Null
$deck | Update-List -Property cards -Remove $player1.cards | Out-Null
$deck | Update-List -Property cards -Remove $player2.cards | Out-Null

$player1.Show()
$player2.Show()
$deck.Show()
```

```Output
Deck :  4♦ 7♥ J♦ 5♣ A♣ 8♦ J♣ Q♥ 6♦ 3♦ 9♦ 6♣ 2♣
        K♥ 4♠ 10♥ 8♠ 10♦ 9♠ 6♠ K♦ 7♣ 3♣ Q♣ A♥ Q♠
        3♥ 5♥ 2♦ 5♠ J♥ J♠ 10♣ 4♥ Q♦ 10♠ 4♣ 2♠ 2♥
        6♥ 7♦ A♠ 5♦ 8♣ 9♥ K♠ 7♠ 3♠ 9♣ A♦ K♣ 8♥

Player 1 :  4♦ J♦ A♣ J♣ 6♦

Player 2 :  7♥ 5♣ 8♦ Q♥ 3♦

Deck :  9♦ 6♣ 2♣ K♥ 4♠ 10♥ 8♠ 10♦ 9♠ 6♠ K♦ 7♣ 3♣
        Q♣ A♥ Q♠ 3♥ 5♥ 2♦ 5♠ J♥ J♠ 10♣ 4♥ Q♦ 10♠
        4♣ 2♠ 2♥ 6♥ 7♦ A♠ 5♦ 8♣ 9♥ K♠ 7♠ 3♠ 9♣
        A♦ K♣ 8♥
```

La sortie indique l’état du jeu avant que les cartes aient été traitées aux joueurs. Vous pouvez voir que chaque joueur a reçu cinq cartes du jeu. La sortie finale indique l’état du pont après avoir traité les cartes aux joueurs. `Update-List` a été utilisé pour sélectionner les cartes du jeu et les ajouter au regroupement des joueurs. Les cartes des joueurs ont été retirées du jeu à l’aide de `Update-List` .

### Exemple 3 : ajouter et supprimer des éléments dans une même commande

`Update-List` vous permet d’utiliser les paramètres **Ajouter** et **supprimer** dans une même commande. Dans cet exemple, le joueur 1 veut abandonner le `4♦` et `6♦` obtenir deux nouvelles cartes.

```powershell
# Player 1 wants two new cards - remove 2 cards & add 2 cards
$player1 | Update-List -Property cards -Remove $player1.cards[0,4] -Add $deck.cards[0..1] | Out-Null
$player1.Show()

# remove dealt cards from deck
$deck | Update-List -Property cards -Remove $deck.cards[0..1] | Out-Null
$deck.Show()
```

```Output
Player 1 :  J♦ A♣ J♣ 9♦ 6♣

Deck :  2♣ K♥ 4♠ 10♥ 8♠ 10♦ 9♠ 6♠ K♦ 7♣ 3♣ Q♣ A♥
        Q♠ 3♥ 5♥ 2♦ 5♠ J♥ J♠ 10♣ 4♥ Q♦ 10♠ 4♣ 2♠
        2♥ 6♥ 7♦ A♠ 5♦ 8♣ 9♥ K♠ 7♠ 3♠ 9♣ A♦ K♣
        8♥
```

## PARAMETERS

### -Add

Spécifie les valeurs de propriété à ajouter à la collection. Entrez les valeurs dans l'ordre dans lequel elles doivent apparaître dans la collection.

```yaml
Type: System.Object[]
Parameter Sets: AddRemoveSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Spécifie les objets à mettre à jour. Vous pouvez également diriger l’objet à mettre à jour vers `Update-List` .

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

### -Propriété

Spécifie la propriété qui contient la collection en cours de mise à jour. Si vous omettez ce paramètre, `Update-List` retourne un objet qui représente la modification au lieu de modifier l’objet.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Remove

Spécifie les valeurs de propriété à supprimer de la collection.

```yaml
Type: System.Object[]
Parameter Sets: AddRemoveSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Remplacer

Spécifie une nouvelle collection. Ce paramètre remplace tous les éléments de la collection d'origine par les éléments spécifiés par ce paramètre.

```yaml
Type: System.Object[]
Parameter Sets: ReplaceSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Management. Automation. PSObject

Vous pouvez diriger les objets à mettre à jour vers `Update-List` .

## SORTIES

### Objets ou System. Management. Automation. PSListModifier

`Update-List` retourne l’objet mis à jour ou retourne un objet qui représente l’action de mise à jour.

## REMARQUES

## LIENS CONNEXES

[Format-List](Format-List.md)

[Select-Object](Select-Object.md)

