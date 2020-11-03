---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-list?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-List
ms.openlocfilehash: 00ada05f52967c0857cfad63a94cd23c49b69367
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201534"
---
# <span data-ttu-id="3c9a2-103">Update-List</span><span class="sxs-lookup"><span data-stu-id="3c9a2-103">Update-List</span></span>

## <span data-ttu-id="3c9a2-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="3c9a2-104">SYNOPSIS</span></span>
<span data-ttu-id="3c9a2-105">Ajoute et supprime des éléments dans une valeur de propriété qui contient une collection d'objets.</span><span class="sxs-lookup"><span data-stu-id="3c9a2-105">Adds items to and removes items from a property value that contains a collection of objects.</span></span>

## <span data-ttu-id="3c9a2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3c9a2-106">SYNTAX</span></span>

### <span data-ttu-id="3c9a2-107">AddRemoveSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="3c9a2-107">AddRemoveSet (Default)</span></span>

```
Update-List [-Add <Object[]>] [-Remove <Object[]>] [-InputObject <PSObject>] [[-Property] <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="3c9a2-108">ReplaceSet</span><span class="sxs-lookup"><span data-stu-id="3c9a2-108">ReplaceSet</span></span>

```
Update-List -Replace <Object[]> [-InputObject <PSObject>] [[-Property] <String>] [<CommonParameters>]
```

## <span data-ttu-id="3c9a2-109">Description</span><span class="sxs-lookup"><span data-stu-id="3c9a2-109">DESCRIPTION</span></span>

<span data-ttu-id="3c9a2-110">L' `Update-List` applet de commande ajoute, supprime ou remplace des éléments dans une valeur de propriété d’un objet et retourne l’objet mis à jour.</span><span class="sxs-lookup"><span data-stu-id="3c9a2-110">The `Update-List` cmdlet adds, removes, or replaces items in a property value of an object and returns the updated object.</span></span> <span data-ttu-id="3c9a2-111">Cette applet de commande est conçue pour les propriétés qui contiennent des collections d'objets.</span><span class="sxs-lookup"><span data-stu-id="3c9a2-111">This cmdlet is designed for properties that contain collections of objects.</span></span>

<span data-ttu-id="3c9a2-112">Les paramètres **Add** et **Remove** ajoutent et suppriment des éléments individuels dans la collection.</span><span class="sxs-lookup"><span data-stu-id="3c9a2-112">The **Add** and **Remove** parameters add individual items to and remove them from the collection.</span></span>
<span data-ttu-id="3c9a2-113">Le paramètre **Replace** remplace l’intégralité de la collection.</span><span class="sxs-lookup"><span data-stu-id="3c9a2-113">The **Replace** parameter replaces the entire collection.</span></span>

<span data-ttu-id="3c9a2-114">Si vous ne spécifiez pas de propriété dans la commande, `Update-List` retourne un objet qui décrit la mise à jour au lieu de mettre à jour l’objet.</span><span class="sxs-lookup"><span data-stu-id="3c9a2-114">If you do not specify a property in the command, `Update-List` returns an object that describes the update instead of updating the object.</span></span> <span data-ttu-id="3c9a2-115">Vous pouvez envoyer l’objet de mise à jour à des applets de commande qui modifient des objets, tels que des `Set` applets de commande.</span><span class="sxs-lookup"><span data-stu-id="3c9a2-115">You can submit the update object to cmdlets that change objects, such as `Set` cmdlets.</span></span>

<span data-ttu-id="3c9a2-116">Cette applet de commande fonctionne uniquement lorsque la propriété en cours de mise à jour prend en charge l’interface **IList** utilisée par `Update-List` .</span><span class="sxs-lookup"><span data-stu-id="3c9a2-116">This cmdlet works only when the property that is being updated supports the **IList** interface that `Update-List` uses.</span></span> <span data-ttu-id="3c9a2-117">En outre, toutes les `Set` applets de commande acceptant une mise à jour doivent prendre en charge l’interface **IList** .</span><span class="sxs-lookup"><span data-stu-id="3c9a2-117">Also, any `Set` cmdlets that accept an update must support the **IList** interface.</span></span>

<span data-ttu-id="3c9a2-118">Les applets de commande de base qui sont installées avec PowerShell ne prennent pas en charge cette interface.</span><span class="sxs-lookup"><span data-stu-id="3c9a2-118">The core cmdlets that are installed with PowerShell do not support this interface.</span></span> <span data-ttu-id="3c9a2-119">Pour déterminer si une applet de commande prend en charge `Update-List` , consultez la rubrique d’aide sur l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3c9a2-119">To determine whether a cmdlet supports `Update-List`, see the cmdlet Help topic.</span></span>

<span data-ttu-id="3c9a2-120">Cette applet de commande a été réintroduite dans PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="3c9a2-120">This cmdlet was reintroduced in PowerShell 7.</span></span>

## <span data-ttu-id="3c9a2-121">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="3c9a2-121">EXAMPLES</span></span>

### <span data-ttu-id="3c9a2-122">Exemple 1 : ajouter des éléments à une valeur de propriété</span><span class="sxs-lookup"><span data-stu-id="3c9a2-122">Example 1: Add items to a property value</span></span>

<span data-ttu-id="3c9a2-123">Dans cet exemple, nous créons une classe qui représente un jeu de cartes où les cartes sont stockées sous la forme d’un objet de collection de **listes** .</span><span class="sxs-lookup"><span data-stu-id="3c9a2-123">In this example we create a class that represents a deck of cards where the cards are stored as a **List** collection object.</span></span> <span data-ttu-id="3c9a2-124">La méthode **NewDeck ()** utilise `Update-List` pour ajouter un jeu complet de valeurs de carte à la collection de **cartes** .</span><span class="sxs-lookup"><span data-stu-id="3c9a2-124">The **NewDeck()** method uses `Update-List`to add a complete deck of card values to the **cards** collection.</span></span>

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
> <span data-ttu-id="3c9a2-125">L' `Update-List` applet de commande génère l’objet mis à jour dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="3c9a2-125">The `Update-List` cmdlet outputs the updated object to the pipeline.</span></span> <span data-ttu-id="3c9a2-126">Nous allons diriger la sortie vers `Out-Null` pour supprimer l’affichage indésirable.</span><span class="sxs-lookup"><span data-stu-id="3c9a2-126">We pipe the output to `Out-Null` to suppress the unwanted display.</span></span>

### <span data-ttu-id="3c9a2-127">Exemple 2 : ajouter et supprimer des éléments d’une propriété de collection</span><span class="sxs-lookup"><span data-stu-id="3c9a2-127">Example 2: Add and remove items of a collection property</span></span>

<span data-ttu-id="3c9a2-128">Si vous continuez avec le code de l’exemple 1, nous allons créer des instances de la classe **Cards** pour représenter un jeu de cartes et les cartes détenues par deux joueurs.</span><span class="sxs-lookup"><span data-stu-id="3c9a2-128">Continuing with the code in Example 1, we will create instances of the **Cards** class to represent a deck of cards and the cards held by two players.</span></span> <span data-ttu-id="3c9a2-129">Nous utilisons l' `Update-List` applet de commande pour ajouter des cartes aux mains des joueurs et pour supprimer des cartes du jeu.</span><span class="sxs-lookup"><span data-stu-id="3c9a2-129">We use the `Update-List` cmdlet to add cards to the players' hands and to remove cards from the deck.</span></span>

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

<span data-ttu-id="3c9a2-130">La sortie indique l’état du jeu avant que les cartes aient été traitées aux joueurs.</span><span class="sxs-lookup"><span data-stu-id="3c9a2-130">The output shows the state of the deck before the cards were dealt to the players.</span></span> <span data-ttu-id="3c9a2-131">Vous pouvez voir que chaque joueur a reçu cinq cartes du jeu.</span><span class="sxs-lookup"><span data-stu-id="3c9a2-131">You can see that each player received five cards from the deck.</span></span> <span data-ttu-id="3c9a2-132">La sortie finale indique l’état du pont après avoir traité les cartes aux joueurs.</span><span class="sxs-lookup"><span data-stu-id="3c9a2-132">The final output shows the state of the deck after dealing the cards to the players.</span></span> <span data-ttu-id="3c9a2-133">`Update-List` a été utilisé pour sélectionner les cartes du jeu et les ajouter au regroupement des joueurs.</span><span class="sxs-lookup"><span data-stu-id="3c9a2-133">`Update-List` was used to select the cards from the deck and add them to the players' collection.</span></span> <span data-ttu-id="3c9a2-134">Les cartes des joueurs ont été retirées du jeu à l’aide de `Update-List` .</span><span class="sxs-lookup"><span data-stu-id="3c9a2-134">Then the players' cards were removed from the deck using `Update-List`.</span></span>

### <span data-ttu-id="3c9a2-135">Exemple 3 : ajouter et supprimer des éléments dans une même commande</span><span class="sxs-lookup"><span data-stu-id="3c9a2-135">Example 3: Add and remove items in a single command</span></span>

<span data-ttu-id="3c9a2-136">`Update-List` vous permet d’utiliser les paramètres **Ajouter** et **supprimer** dans une même commande.</span><span class="sxs-lookup"><span data-stu-id="3c9a2-136">`Update-List` allows you to use the **Add** and **Remove** parameters in a single command.</span></span> <span data-ttu-id="3c9a2-137">Dans cet exemple, le joueur 1 veut abandonner le `4♦` et `6♦` obtenir deux nouvelles cartes.</span><span class="sxs-lookup"><span data-stu-id="3c9a2-137">In this example, Player 1 wants to discard the `4♦` and `6♦` and get two new cards.</span></span>

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

## <span data-ttu-id="3c9a2-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3c9a2-138">PARAMETERS</span></span>

### <span data-ttu-id="3c9a2-139">-Add</span><span class="sxs-lookup"><span data-stu-id="3c9a2-139">-Add</span></span>

<span data-ttu-id="3c9a2-140">Spécifie les valeurs de propriété à ajouter à la collection.</span><span class="sxs-lookup"><span data-stu-id="3c9a2-140">Specifies the property values to be added to the collection.</span></span> <span data-ttu-id="3c9a2-141">Entrez les valeurs dans l'ordre dans lequel elles doivent apparaître dans la collection.</span><span class="sxs-lookup"><span data-stu-id="3c9a2-141">Enter the values in the order that they should appear in the collection.</span></span>

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

### <span data-ttu-id="3c9a2-142">-InputObject</span><span class="sxs-lookup"><span data-stu-id="3c9a2-142">-InputObject</span></span>

<span data-ttu-id="3c9a2-143">Spécifie les objets à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="3c9a2-143">Specifies the objects to be updated.</span></span> <span data-ttu-id="3c9a2-144">Vous pouvez également diriger l’objet à mettre à jour vers `Update-List` .</span><span class="sxs-lookup"><span data-stu-id="3c9a2-144">You can also pipe the object to be updated to `Update-List`.</span></span>

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

### <span data-ttu-id="3c9a2-145">-Propriété</span><span class="sxs-lookup"><span data-stu-id="3c9a2-145">-Property</span></span>

<span data-ttu-id="3c9a2-146">Spécifie la propriété qui contient la collection en cours de mise à jour.</span><span class="sxs-lookup"><span data-stu-id="3c9a2-146">Specifies the property that contains the collection that is being updated.</span></span> <span data-ttu-id="3c9a2-147">Si vous omettez ce paramètre, `Update-List` retourne un objet qui représente la modification au lieu de modifier l’objet.</span><span class="sxs-lookup"><span data-stu-id="3c9a2-147">If you omit this parameter, `Update-List` returns an object that represents the change instead of changing the object.</span></span>

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

### <span data-ttu-id="3c9a2-148">-Remove</span><span class="sxs-lookup"><span data-stu-id="3c9a2-148">-Remove</span></span>

<span data-ttu-id="3c9a2-149">Spécifie les valeurs de propriété à supprimer de la collection.</span><span class="sxs-lookup"><span data-stu-id="3c9a2-149">Specifies the property values to be removed from the collection.</span></span>

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

### <span data-ttu-id="3c9a2-150">-Remplacer</span><span class="sxs-lookup"><span data-stu-id="3c9a2-150">-Replace</span></span>

<span data-ttu-id="3c9a2-151">Spécifie une nouvelle collection.</span><span class="sxs-lookup"><span data-stu-id="3c9a2-151">Specifies a new collection.</span></span> <span data-ttu-id="3c9a2-152">Ce paramètre remplace tous les éléments de la collection d'origine par les éléments spécifiés par ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="3c9a2-152">This parameter replaces all items in the original collection with the items specified by this parameter.</span></span>

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

### <span data-ttu-id="3c9a2-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3c9a2-153">CommonParameters</span></span>

<span data-ttu-id="3c9a2-154">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3c9a2-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3c9a2-155">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3c9a2-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3c9a2-156">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="3c9a2-156">INPUTS</span></span>

### <span data-ttu-id="3c9a2-157">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="3c9a2-157">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="3c9a2-158">Vous pouvez diriger les objets à mettre à jour vers `Update-List` .</span><span class="sxs-lookup"><span data-stu-id="3c9a2-158">You can pipe the objects to be updated to `Update-List`.</span></span>

## <span data-ttu-id="3c9a2-159">SORTIES</span><span class="sxs-lookup"><span data-stu-id="3c9a2-159">OUTPUTS</span></span>

### <span data-ttu-id="3c9a2-160">Objets ou System. Management. Automation. PSListModifier</span><span class="sxs-lookup"><span data-stu-id="3c9a2-160">Objects or System.Management.Automation.PSListModifier</span></span>

<span data-ttu-id="3c9a2-161">`Update-List` retourne l’objet mis à jour ou retourne un objet qui représente l’action de mise à jour.</span><span class="sxs-lookup"><span data-stu-id="3c9a2-161">`Update-List` returns the updated object, or it returns an object that represents the update action.</span></span>

## <span data-ttu-id="3c9a2-162">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="3c9a2-162">NOTES</span></span>

## <span data-ttu-id="3c9a2-163">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="3c9a2-163">RELATED LINKS</span></span>

[<span data-ttu-id="3c9a2-164">Format-List</span><span class="sxs-lookup"><span data-stu-id="3c9a2-164">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="3c9a2-165">Select-Object</span><span class="sxs-lookup"><span data-stu-id="3c9a2-165">Select-Object</span></span>](Select-Object.md)
