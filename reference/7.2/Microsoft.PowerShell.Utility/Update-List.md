---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-list?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-List
ms.openlocfilehash: ae473541770948dee1ce927ddee45bd806d8ff29
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596317"
---
# <span data-ttu-id="d103d-102">Update-List</span><span class="sxs-lookup"><span data-stu-id="d103d-102">Update-List</span></span>

## <span data-ttu-id="d103d-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d103d-103">SYNOPSIS</span></span>
<span data-ttu-id="d103d-104">Ajoute et supprime des éléments dans une valeur de propriété qui contient une collection d'objets.</span><span class="sxs-lookup"><span data-stu-id="d103d-104">Adds items to and removes items from a property value that contains a collection of objects.</span></span>

## <span data-ttu-id="d103d-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="d103d-105">SYNTAX</span></span>

### <span data-ttu-id="d103d-106">AddRemoveSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="d103d-106">AddRemoveSet (Default)</span></span>

```
Update-List [-Add <Object[]>] [-Remove <Object[]>] [-InputObject <PSObject>] [[-Property] <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="d103d-107">ReplaceSet</span><span class="sxs-lookup"><span data-stu-id="d103d-107">ReplaceSet</span></span>

```
Update-List -Replace <Object[]> [-InputObject <PSObject>] [[-Property] <String>] [<CommonParameters>]
```

## <span data-ttu-id="d103d-108">Description</span><span class="sxs-lookup"><span data-stu-id="d103d-108">DESCRIPTION</span></span>

<span data-ttu-id="d103d-109">L' `Update-List` applet de commande ajoute, supprime ou remplace des éléments dans une valeur de propriété d’un objet et retourne l’objet mis à jour.</span><span class="sxs-lookup"><span data-stu-id="d103d-109">The `Update-List` cmdlet adds, removes, or replaces items in a property value of an object and returns the updated object.</span></span> <span data-ttu-id="d103d-110">Cette applet de commande est conçue pour les propriétés qui contiennent des collections d'objets.</span><span class="sxs-lookup"><span data-stu-id="d103d-110">This cmdlet is designed for properties that contain collections of objects.</span></span>

<span data-ttu-id="d103d-111">Les paramètres **Add** et **Remove** ajoutent et suppriment des éléments individuels dans la collection.</span><span class="sxs-lookup"><span data-stu-id="d103d-111">The **Add** and **Remove** parameters add individual items to and remove them from the collection.</span></span>
<span data-ttu-id="d103d-112">Le paramètre **Replace** remplace l’intégralité de la collection.</span><span class="sxs-lookup"><span data-stu-id="d103d-112">The **Replace** parameter replaces the entire collection.</span></span>

<span data-ttu-id="d103d-113">Si vous ne spécifiez pas de propriété dans la commande, `Update-List` retourne un objet qui décrit la mise à jour au lieu de mettre à jour l’objet.</span><span class="sxs-lookup"><span data-stu-id="d103d-113">If you do not specify a property in the command, `Update-List` returns an object that describes the update instead of updating the object.</span></span> <span data-ttu-id="d103d-114">Vous pouvez envoyer l’objet de mise à jour à des applets de commande qui modifient des objets, tels que des `Set` applets de commande.</span><span class="sxs-lookup"><span data-stu-id="d103d-114">You can submit the update object to cmdlets that change objects, such as `Set` cmdlets.</span></span>

<span data-ttu-id="d103d-115">Cette applet de commande fonctionne uniquement lorsque la propriété en cours de mise à jour prend en charge l’interface **IList** utilisée par `Update-List` .</span><span class="sxs-lookup"><span data-stu-id="d103d-115">This cmdlet works only when the property that is being updated supports the **IList** interface that `Update-List` uses.</span></span> <span data-ttu-id="d103d-116">En outre, toutes les `Set` applets de commande acceptant une mise à jour doivent prendre en charge l’interface **IList** .</span><span class="sxs-lookup"><span data-stu-id="d103d-116">Also, any `Set` cmdlets that accept an update must support the **IList** interface.</span></span>

<span data-ttu-id="d103d-117">Les applets de commande de base qui sont installées avec PowerShell ne prennent pas en charge cette interface.</span><span class="sxs-lookup"><span data-stu-id="d103d-117">The core cmdlets that are installed with PowerShell do not support this interface.</span></span> <span data-ttu-id="d103d-118">Pour déterminer si une applet de commande prend en charge `Update-List` , consultez la rubrique d’aide sur l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d103d-118">To determine whether a cmdlet supports `Update-List`, see the cmdlet Help topic.</span></span>

<span data-ttu-id="d103d-119">Cette applet de commande a été réintroduite dans PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="d103d-119">This cmdlet was reintroduced in PowerShell 7.</span></span>

## <span data-ttu-id="d103d-120">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d103d-120">EXAMPLES</span></span>

### <span data-ttu-id="d103d-121">Exemple 1 : ajouter des éléments à une valeur de propriété</span><span class="sxs-lookup"><span data-stu-id="d103d-121">Example 1: Add items to a property value</span></span>

<span data-ttu-id="d103d-122">Dans cet exemple, nous créons une classe qui représente un jeu de cartes où les cartes sont stockées sous la forme d’un objet de collection de **listes** .</span><span class="sxs-lookup"><span data-stu-id="d103d-122">In this example we create a class that represents a deck of cards where the cards are stored as a **List** collection object.</span></span> <span data-ttu-id="d103d-123">La méthode **NewDeck ()** utilise `Update-List` pour ajouter un jeu complet de valeurs de carte à la collection de **cartes** .</span><span class="sxs-lookup"><span data-stu-id="d103d-123">The **NewDeck()** method uses `Update-List`to add a complete deck of card values to the **cards** collection.</span></span>

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
> <span data-ttu-id="d103d-124">L' `Update-List` applet de commande génère l’objet mis à jour dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="d103d-124">The `Update-List` cmdlet outputs the updated object to the pipeline.</span></span> <span data-ttu-id="d103d-125">Nous allons diriger la sortie vers `Out-Null` pour supprimer l’affichage indésirable.</span><span class="sxs-lookup"><span data-stu-id="d103d-125">We pipe the output to `Out-Null` to suppress the unwanted display.</span></span>

### <span data-ttu-id="d103d-126">Exemple 2 : ajouter et supprimer des éléments d’une propriété de collection</span><span class="sxs-lookup"><span data-stu-id="d103d-126">Example 2: Add and remove items of a collection property</span></span>

<span data-ttu-id="d103d-127">Si vous continuez avec le code de l’exemple 1, nous allons créer des instances de la classe **Cards** pour représenter un jeu de cartes et les cartes détenues par deux joueurs.</span><span class="sxs-lookup"><span data-stu-id="d103d-127">Continuing with the code in Example 1, we will create instances of the **Cards** class to represent a deck of cards and the cards held by two players.</span></span> <span data-ttu-id="d103d-128">Nous utilisons l' `Update-List` applet de commande pour ajouter des cartes aux mains des joueurs et pour supprimer des cartes du jeu.</span><span class="sxs-lookup"><span data-stu-id="d103d-128">We use the `Update-List` cmdlet to add cards to the players' hands and to remove cards from the deck.</span></span>

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

<span data-ttu-id="d103d-129">La sortie indique l’état du jeu avant que les cartes aient été traitées aux joueurs.</span><span class="sxs-lookup"><span data-stu-id="d103d-129">The output shows the state of the deck before the cards were dealt to the players.</span></span> <span data-ttu-id="d103d-130">Vous pouvez voir que chaque joueur a reçu cinq cartes du jeu.</span><span class="sxs-lookup"><span data-stu-id="d103d-130">You can see that each player received five cards from the deck.</span></span> <span data-ttu-id="d103d-131">La sortie finale indique l’état du pont après avoir traité les cartes aux joueurs.</span><span class="sxs-lookup"><span data-stu-id="d103d-131">The final output shows the state of the deck after dealing the cards to the players.</span></span> <span data-ttu-id="d103d-132">`Update-List` a été utilisé pour sélectionner les cartes du jeu et les ajouter au regroupement des joueurs.</span><span class="sxs-lookup"><span data-stu-id="d103d-132">`Update-List` was used to select the cards from the deck and add them to the players' collection.</span></span> <span data-ttu-id="d103d-133">Les cartes des joueurs ont été retirées du jeu à l’aide de `Update-List` .</span><span class="sxs-lookup"><span data-stu-id="d103d-133">Then the players' cards were removed from the deck using `Update-List`.</span></span>

### <span data-ttu-id="d103d-134">Exemple 3 : ajouter et supprimer des éléments dans une même commande</span><span class="sxs-lookup"><span data-stu-id="d103d-134">Example 3: Add and remove items in a single command</span></span>

<span data-ttu-id="d103d-135">`Update-List` vous permet d’utiliser les paramètres **Ajouter** et **supprimer** dans une même commande.</span><span class="sxs-lookup"><span data-stu-id="d103d-135">`Update-List` allows you to use the **Add** and **Remove** parameters in a single command.</span></span> <span data-ttu-id="d103d-136">Dans cet exemple, le joueur 1 veut abandonner le `4♦` et `6♦` obtenir deux nouvelles cartes.</span><span class="sxs-lookup"><span data-stu-id="d103d-136">In this example, Player 1 wants to discard the `4♦` and `6♦` and get two new cards.</span></span>

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

## <span data-ttu-id="d103d-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d103d-137">PARAMETERS</span></span>

### <span data-ttu-id="d103d-138">-Add</span><span class="sxs-lookup"><span data-stu-id="d103d-138">-Add</span></span>

<span data-ttu-id="d103d-139">Spécifie les valeurs de propriété à ajouter à la collection.</span><span class="sxs-lookup"><span data-stu-id="d103d-139">Specifies the property values to be added to the collection.</span></span> <span data-ttu-id="d103d-140">Entrez les valeurs dans l'ordre dans lequel elles doivent apparaître dans la collection.</span><span class="sxs-lookup"><span data-stu-id="d103d-140">Enter the values in the order that they should appear in the collection.</span></span>

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

### <span data-ttu-id="d103d-141">-InputObject</span><span class="sxs-lookup"><span data-stu-id="d103d-141">-InputObject</span></span>

<span data-ttu-id="d103d-142">Spécifie les objets à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="d103d-142">Specifies the objects to be updated.</span></span> <span data-ttu-id="d103d-143">Vous pouvez également diriger l’objet à mettre à jour vers `Update-List` .</span><span class="sxs-lookup"><span data-stu-id="d103d-143">You can also pipe the object to be updated to `Update-List`.</span></span>

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

### <span data-ttu-id="d103d-144">-Propriété</span><span class="sxs-lookup"><span data-stu-id="d103d-144">-Property</span></span>

<span data-ttu-id="d103d-145">Spécifie la propriété qui contient la collection en cours de mise à jour.</span><span class="sxs-lookup"><span data-stu-id="d103d-145">Specifies the property that contains the collection that is being updated.</span></span> <span data-ttu-id="d103d-146">Si vous omettez ce paramètre, `Update-List` retourne un objet qui représente la modification au lieu de modifier l’objet.</span><span class="sxs-lookup"><span data-stu-id="d103d-146">If you omit this parameter, `Update-List` returns an object that represents the change instead of changing the object.</span></span>

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

### <span data-ttu-id="d103d-147">-Remove</span><span class="sxs-lookup"><span data-stu-id="d103d-147">-Remove</span></span>

<span data-ttu-id="d103d-148">Spécifie les valeurs de propriété à supprimer de la collection.</span><span class="sxs-lookup"><span data-stu-id="d103d-148">Specifies the property values to be removed from the collection.</span></span>

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

### <span data-ttu-id="d103d-149">-Remplacer</span><span class="sxs-lookup"><span data-stu-id="d103d-149">-Replace</span></span>

<span data-ttu-id="d103d-150">Spécifie une nouvelle collection.</span><span class="sxs-lookup"><span data-stu-id="d103d-150">Specifies a new collection.</span></span> <span data-ttu-id="d103d-151">Ce paramètre remplace tous les éléments de la collection d'origine par les éléments spécifiés par ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="d103d-151">This parameter replaces all items in the original collection with the items specified by this parameter.</span></span>

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

### <span data-ttu-id="d103d-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d103d-152">CommonParameters</span></span>

<span data-ttu-id="d103d-153">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d103d-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d103d-154">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d103d-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d103d-155">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d103d-155">INPUTS</span></span>

### <span data-ttu-id="d103d-156">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="d103d-156">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="d103d-157">Vous pouvez diriger les objets à mettre à jour vers `Update-List` .</span><span class="sxs-lookup"><span data-stu-id="d103d-157">You can pipe the objects to be updated to `Update-List`.</span></span>

## <span data-ttu-id="d103d-158">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d103d-158">OUTPUTS</span></span>

### <span data-ttu-id="d103d-159">Objets ou System. Management. Automation. PSListModifier</span><span class="sxs-lookup"><span data-stu-id="d103d-159">Objects or System.Management.Automation.PSListModifier</span></span>

<span data-ttu-id="d103d-160">`Update-List` retourne l’objet mis à jour ou retourne un objet qui représente l’action de mise à jour.</span><span class="sxs-lookup"><span data-stu-id="d103d-160">`Update-List` returns the updated object, or it returns an object that represents the update action.</span></span>

## <span data-ttu-id="d103d-161">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d103d-161">NOTES</span></span>

## <span data-ttu-id="d103d-162">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d103d-162">RELATED LINKS</span></span>

[<span data-ttu-id="d103d-163">Format-List</span><span class="sxs-lookup"><span data-stu-id="d103d-163">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="d103d-164">Select-Object</span><span class="sxs-lookup"><span data-stu-id="d103d-164">Select-Object</span></span>](Select-Object.md)

