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
# <a name="about_hidden"></a>about_Hidden

## <a name="short-description"></a>DESCRIPTION COURTE
Décrit le mot clé Hidden, qui masque les membres de la classe par défaut Get-Member résultats.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Quand vous utilisez le mot clé Hidden dans un script, vous masquez les membres d’une classe par défaut. Le mot clé Hidden peut masquer des propriétés, des méthodes (notamment des constructeurs, des événements, des propriétés d’alias et d’autres types de membres, y compris des membres statiques, des résultats par défaut de l’applet de commande Get-Member et des résultats IntelliSense et de saisie semi-automatique par tabulation. Pour afficher les membres que vous avez masqués à l’aide du mot clé Hidden, ajoutez le paramètre-force à une commande Get-Member.

Les membres masqués ne sont pas affichés à l’aide de la saisie semi-automatique par tabulation ou IntelliSense, sauf si la saisie semi-automatique se produit dans la classe qui définit le membre masqué.

Un nouvel attribut, System. Management. Automation. Hiddenattribute,, a été ajouté, afin que \# le code C puisse avoir la même sémantique dans PowerShell.

Le mot clé Hidden est utile pour créer des propriétés et des méthodes dans une classe que vous ne souhaitez pas que les autres utilisateurs de la classe voient, ou puissent être facilement modifiables.

Le mot clé Hidden n’a aucun effet sur la façon dont vous pouvez afficher ou modifier les membres d’une classe. Comme tous les mots clés de langage dans PowerShell, Hidden n’est pas sensible à la casse et les membres masqués sont toujours publics.

Masqué, avec les classes personnalisées, a été introduit dans PowerShell 5,0.

## <a name="example"></a>EXEMPLE

L’exemple suivant montre comment utiliser le mot clé Hidden dans une définition de classe. La méthode de classe car, dispose d’une propriété, qui n’a pas besoin d’être affichée ou modifiée (il s’agit simplement du nombre de fois où le lecteur est appelé sur la classe car, d’une mesure qui n’est pas importante pour les utilisateurs de la classe ; par exemple, si vous achetez une voiture, vous ne demandez pas au vendeur le nombre de lecteurs de la voiture.

Étant donné que les utilisateurs de la classe n’ont pas besoin de modifier cette propriété, nous pouvons masquer la propriété à partir de Get-Member et des résultats de saisie semi-automatique à l’aide du mot clé Hidden.

Ajoutez le mot clé Hidden en l’entrant sur la même ligne d’instruction que la propriété et son type de données. Bien que le mot clé puisse être dans n’importe quel ordre sur cette ligne, le fait de démarrer l’instruction avec le mot clé Hidden facilite l’identification de tous les membres que vous avez masqués plus tard.

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

À présent, créez une nouvelle instance de la classe car, puis enregistrez-la dans une variable, \$ TestCar.

```powershell
$TestCar = [Car]::new()
```

Une fois que vous avez créé la nouvelle instance, dirigez le contenu de la variable $TestCar vers l’élément-Member. Notez que la propriété de passes ne fait pas partie des membres listés dans les résultats de la commande Get-Member.

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

Essayez à présent d’exécuter Get-Member, mais cette fois-ci, ajoutez le paramètre-force.
Notez que les résultats contiennent la propriété éléments masqués, parmi d’autres membres qui sont masqués par défaut.

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

## <a name="see-also"></a>VOIR AUSSI

[À propos des classes](about_Classes.md)

[about_Language_Keywords](about_Language_Keywords.md)

[about_Wildcards](about_Wildcards.md)

[Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member)

