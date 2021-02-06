---
description: Décrit le mot clé Hidden, qui masque les membres de la classe par défaut Get-Member résultats.
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_hidden?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Hidden
ms.openlocfilehash: 8340a955b7cfa540baccde0da233d6d9cf0c5552
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595478"
---
# <a name="about_hidden"></a><span data-ttu-id="35003-103">about_Hidden</span><span class="sxs-lookup"><span data-stu-id="35003-103">about_Hidden</span></span>

## <a name="short-description"></a><span data-ttu-id="35003-104">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="35003-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="35003-105">Décrit le mot clé Hidden, qui masque les membres de la classe par défaut Get-Member résultats.</span><span class="sxs-lookup"><span data-stu-id="35003-105">Describes the Hidden keyword, which hides class members from default Get-Member results.</span></span>

## <a name="long-description"></a><span data-ttu-id="35003-106">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="35003-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="35003-107">Quand vous utilisez le mot clé Hidden dans un script, vous masquez les membres d’une classe par défaut.</span><span class="sxs-lookup"><span data-stu-id="35003-107">When you use the Hidden keyword in a script, you hide the members of a class by default.</span></span> <span data-ttu-id="35003-108">Le mot clé Hidden peut masquer des propriétés, des méthodes (notamment des constructeurs, des événements, des propriétés d’alias et d’autres types de membres, y compris des membres statiques, des résultats par défaut de l’applet de commande Get-Member et des résultats IntelliSense et de saisie semi-automatique par tabulation.</span><span class="sxs-lookup"><span data-stu-id="35003-108">The Hidden keyword can hide properties, methods (including constructors, events, alias properties, and other member types, including static members, from the default results of the Get-Member cmdlet, and from IntelliSense and tab completion results.</span></span> <span data-ttu-id="35003-109">Pour afficher les membres que vous avez masqués à l’aide du mot clé Hidden, ajoutez le paramètre-force à une commande Get-Member.</span><span class="sxs-lookup"><span data-stu-id="35003-109">To display members that you have hidden with the Hidden keyword, add the -Force parameter to a Get-Member command.</span></span>

<span data-ttu-id="35003-110">Les membres masqués ne sont pas affichés à l’aide de la saisie semi-automatique par tabulation ou IntelliSense, sauf si la saisie semi-automatique se produit dans la classe qui définit le membre masqué.</span><span class="sxs-lookup"><span data-stu-id="35003-110">Hidden members are not displayed by using tab completion or IntelliSense, unless the completion occurs in the class that defines the hidden member.</span></span>

<span data-ttu-id="35003-111">Un nouvel attribut, System. Management. Automation. Hiddenattribute,, a été ajouté, afin que \# le code C puisse avoir la même sémantique dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="35003-111">A new attribute, System.Management.Automation.HiddenAttribute, has been added, so that C\# code can have the same semantics within PowerShell.</span></span>

<span data-ttu-id="35003-112">Le mot clé Hidden est utile pour créer des propriétés et des méthodes dans une classe que vous ne souhaitez pas que les autres utilisateurs de la classe voient, ou puissent être facilement modifiables.</span><span class="sxs-lookup"><span data-stu-id="35003-112">The Hidden keyword is useful for creating properties and methods within a class that you do not necessarily want other users of the class to see, or readily be able to edit.</span></span>

<span data-ttu-id="35003-113">Le mot clé Hidden n’a aucun effet sur la façon dont vous pouvez afficher ou modifier les membres d’une classe.</span><span class="sxs-lookup"><span data-stu-id="35003-113">The Hidden keyword has no effect on how you can view or make changes to members of a class.</span></span> <span data-ttu-id="35003-114">Comme tous les mots clés de langage dans PowerShell, Hidden n’est pas sensible à la casse et les membres masqués sont toujours publics.</span><span class="sxs-lookup"><span data-stu-id="35003-114">Like all language keywords in PowerShell, Hidden is not case-sensitive, and hidden members are still public.</span></span>

<span data-ttu-id="35003-115">Masqué, avec les classes personnalisées, a été introduit dans PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="35003-115">Hidden, along with custom classes, was introduced in PowerShell 5.0.</span></span>

## <a name="example"></a><span data-ttu-id="35003-116">EXEMPLE</span><span class="sxs-lookup"><span data-stu-id="35003-116">EXAMPLE</span></span>

<span data-ttu-id="35003-117">L’exemple suivant montre comment utiliser le mot clé Hidden dans une définition de classe.</span><span class="sxs-lookup"><span data-stu-id="35003-117">The following example shows how to use the Hidden keyword in a class definition.</span></span> <span data-ttu-id="35003-118">La méthode de classe car, dispose d’une propriété, qui n’a pas besoin d’être affichée ou modifiée (il s’agit simplement du nombre de fois où le lecteur est appelé sur la classe car, d’une mesure qui n’est pas importante pour les utilisateurs de la classe ; par exemple, si vous achetez une voiture, vous ne demandez pas au vendeur le nombre de lecteurs de la voiture.</span><span class="sxs-lookup"><span data-stu-id="35003-118">The Car class method, Drive, has a property, rides, that does not need to be viewed or changed (it merely tallies the number of times that Drive is called on the Car class, a metric that is not important to users of the class; consider, for example, that when you are buying a car, you do not ask the seller on how many drives the car has been taken.</span></span>

<span data-ttu-id="35003-119">Étant donné que les utilisateurs de la classe n’ont pas besoin de modifier cette propriété, nous pouvons masquer la propriété à partir de Get-Member et des résultats de saisie semi-automatique à l’aide du mot clé Hidden.</span><span class="sxs-lookup"><span data-stu-id="35003-119">Because there is little need for users of the class to change this property, we can hide the property from Get-Member and automatic completion results by using the Hidden keyword.</span></span>

<span data-ttu-id="35003-120">Ajoutez le mot clé Hidden en l’entrant sur la même ligne d’instruction que la propriété et son type de données.</span><span class="sxs-lookup"><span data-stu-id="35003-120">Add the Hidden keyword by entering it on the same statement line as the property and its data type.</span></span> <span data-ttu-id="35003-121">Bien que le mot clé puisse être dans n’importe quel ordre sur cette ligne, le fait de démarrer l’instruction avec le mot clé Hidden facilite l’identification de tous les membres que vous avez masqués plus tard.</span><span class="sxs-lookup"><span data-stu-id="35003-121">Although the keyword can be in any order on this line, starting the statement with the Hidden keyword makes it easier for you later to identify all members that you have hidden.</span></span>

```powershell
class Car
{
   # Properties
   [String] $Color
   [String] $ModelYear
   [int] $Distance

   # Method
   [int] Drive ([int]$miles)
   {
      $this.Distance += $miles
      $this.rides++
      return $this.Distance
   }

   # Hidden property of the Drive method
    hidden [int] $rides = 0
}
```

<span data-ttu-id="35003-122">À présent, créez une nouvelle instance de la classe car, puis enregistrez-la dans une variable, \$ TestCar.</span><span class="sxs-lookup"><span data-stu-id="35003-122">Now, create a new instance of the Car class, and save it in a variable, \$TestCar.</span></span>

```powershell
$TestCar = [Car]::new()
```

<span data-ttu-id="35003-123">Une fois que vous avez créé la nouvelle instance, dirigez le contenu de la variable $TestCar vers l’élément-Member.</span><span class="sxs-lookup"><span data-stu-id="35003-123">After you create the new instance, pipe the contents of the $TestCar variable to Get-Member.</span></span> <span data-ttu-id="35003-124">Notez que la propriété de passes ne fait pas partie des membres listés dans les résultats de la commande Get-Member.</span><span class="sxs-lookup"><span data-stu-id="35003-124">Observe that the rides property is not among the members listed in the Get-Member command results.</span></span>

```output
PS C:\Windows\system32> $TestCar | Get-Member

   TypeName: Car

Name        MemberType Definition
----        ---------- ----------
Drive       Method     int Drive(int miles)
Equals      Method     bool Equals(System.Object obj)
GetHashCode Method     int GetHashCode()
GetType     Method     type GetType()
ToString    Method     string ToString()
Color       Property   string Color {get;set;}
Distance    Property   int Distance {get;set;}
ModelYear   Property   string ModelYear {get;set;}

```

<span data-ttu-id="35003-125">Essayez à présent d’exécuter Get-Member, mais cette fois-ci, ajoutez le paramètre-force.</span><span class="sxs-lookup"><span data-stu-id="35003-125">Now, try running Get-Member again, but this time, add the -Force parameter.</span></span>
<span data-ttu-id="35003-126">Notez que les résultats contiennent la propriété éléments masqués, parmi d’autres membres qui sont masqués par défaut.</span><span class="sxs-lookup"><span data-stu-id="35003-126">Note that the results contain the hidden rides property, among other members that are hidden by default.</span></span>

```output
PS C:\Windows\system32> $TestCar | Get-Member -Force

   TypeName: Car

Name          MemberType   Definition
----          ----------   ----------
pstypenames   CodeProperty System.Collections.ObjectModel.Collection`1
psadapted     MemberSet    psadapted {Color, ModelYear, Distance,
psbase        MemberSet    psbase {Color, ModelYear, Distance,...
psextended    MemberSet    psextended {}
psobject      MemberSet    psobject {BaseObject, Members,...
Drive         Method       int Drive(int miles)
Equals        Method       bool Equals(System.Object obj)
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
get_Color     Method       string get_Color()
get_Distance  Method       int get_Distance()
get_ModelYear Method       string get_ModelYear()
get_rides     Method       int get_rides()
set_Color     Method       void set_Color(string )
set_Distance  Method       void set_Distance(int )
set_ModelYear Method       void set_ModelYear(string )
set_rides     Method       void set_rides(int )
ToString      Method       string ToString()
Color         Property     string Color {get;set;}
Distance      Property     int Distance {get;set;}
ModelYear     Property     string ModelYear {get;set;}
rides         Property     int rides {get;set;}

```

## <a name="see-also"></a><span data-ttu-id="35003-127">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="35003-127">SEE ALSO</span></span>

[<span data-ttu-id="35003-128">À propos des classes</span><span class="sxs-lookup"><span data-stu-id="35003-128">about_Classes</span></span>](about_Classes.md)

[<span data-ttu-id="35003-129">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="35003-129">about_Language_Keywords</span></span>](about_Language_Keywords.md)

[<span data-ttu-id="35003-130">about_Wildcards</span><span class="sxs-lookup"><span data-stu-id="35003-130">about_Wildcards</span></span>](about_Wildcards.md)

[<span data-ttu-id="35003-131">Get-Member</span><span class="sxs-lookup"><span data-stu-id="35003-131">Get-Member</span></span>](xref:Microsoft.PowerShell.Utility.Get-Member)

