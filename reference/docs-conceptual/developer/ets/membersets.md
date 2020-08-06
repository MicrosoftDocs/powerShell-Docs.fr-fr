---
title: Jeux de membres du système de type étendu
ms.date: 07/09/2020
ms.openlocfilehash: 3f4e44ed7b498bb7c4a71f7b131270ed4f2ef981
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786252"
---
# <a name="ets-member-sets"></a>Jeux de membres ETS

Les jeux de membres vous permettent de partitionner les membres de l’objet **PSObject** en deux sous-ensembles afin que les membres des sous-ensembles puissent être référencés ensemble par leur nom de sous-ensemble. Les deux types de sous-ensembles incluent les jeux de propriétés et les jeux de membres. Par exemple, si PowerShell utilise des jeux de membres, un jeu de propriétés spécifique nommé **DefaultDisplayPropertySet** est utilisé pour déterminer, au moment de l’exécution, les propriétés à afficher pour un objet **PSObject** donné.

## <a name="property-sets"></a>Jeux de propriétés

Les jeux de propriétés peuvent inclure n’importe quel nombre de propriétés d’un type **PSObject** . En général, un jeu de propriétés peut être utilisé chaque fois qu’une collection de propriétés (du même type) est nécessaire. Le jeu de propriétés est créé en appelant le `PSPropertySet(System.String,System.Collections.Generic.IEnumerable{System.String})` constructeur avec le nom du jeu de propriétés et les noms des propriétés référencées. L’objet **PSPropertySet** créé peut ensuite être utilisé en tant qu’alias qui pointe vers les propriétés du jeu. La classe [PSPropertySet](/dotnet/api/system.management.automation.pspropertyset) a les propriétés et méthodes suivantes.

- Propriété **isInstance** : obtient une valeur **booléenne** qui indique la source de la propriété.
- Propriété **MemberType** : obtient le type des propriétés dans le jeu de propriétés.
- **Name** , propriété : obtient le nom du jeu de propriétés.
- Propriété **ReferencedPropertyNames** : obtient les noms des propriétés dans le jeu de propriétés.
- Propriété **TypeNameOfValue** : obtient une constante d’énumération **PropertySet** qui définit ce jeu comme un jeu de propriétés.
- Propriété **value** : Obtient ou définit l’objet **PSPropertySet** .
- `PSPropertySet.Copy`méthode : effectue une copie exacte de l’objet **PSPropertySet** .
- `PSMemberSet.ToString`méthode : convertit l’objet **PSPropertySet** en chaîne.

## <a name="member-sets"></a>Jeux de membres

Les jeux de membres peuvent inclure n’importe quel nombre de membres étendus de n’importe quel type. Le jeu de membres est créé en appelant la`PSMemberSet(System.String,System.Collections.Generic.IEnumerable{System.Management.Automation.PSMemberInfo})`
constructeur avec le nom du jeu de membres et les noms des membres référencés. L’objet **PSPropertySet** créé peut ensuite être utilisé en tant qu’alias qui pointe vers les membres du jeu. La classe [PSMemberSet](/dotnet/api/system.management.automation.psmemberset) a les propriétés et méthodes suivantes.

- Propriété **isInstance** : obtient une valeur **booléenne** qui indique la source du membre.
- **Members** , propriété : obtient tous les membres du jeu de membres.
- Propriété **MemberType** : obtient une constante d’énumération **MemberSet** qui définit ce jeu en tant que jeu de membres.
- **Methods** , propriété : obtient les méthodes incluses dans le jeu de membres.
- Propriété **Properties** : obtient les propriétés incluses dans le jeu de membres.
- Propriété **TypeNameOfValue** : obtient une constante d’énumération **MemberSet** qui définit ce jeu en tant que jeu de membres.
- Propriété **value** : obtient l’objet **PSMemberSet** .
- `PSMemberSet.Copy`méthode : effectue une copie exacte de l’objet **PSMemberSet** .
- `PSMemberSet.ToString`méthode : convertit l’objet **PSMemberSet** en chaîne.
