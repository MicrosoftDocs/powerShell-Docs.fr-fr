---
ms.date: 09/12/2016
ms.topic: reference
title: Guide pratique pour ajouter la syntaxe à une rubrique d’aide d’applet de commande
description: Guide pratique pour ajouter la syntaxe à une rubrique d’aide d’applet de commande
ms.openlocfilehash: bcc037d22051c162cd0f70702da17afe7ed9c01a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659066"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a>Guide pratique pour ajouter la syntaxe à une rubrique d’aide d’applet de commande

Avant de commencer à coder le XML pour le diagramme de syntaxe dans le fichier d’aide de l’applet de commande, lisez cette section pour obtenir une image claire du type de données que vous devez fournir, telles que les attributs des paramètres, et de la façon dont ces données sont affichées dans le diagramme de syntaxe..

## <a name="parameter-attributes"></a>Attributs de paramètre

- Obligatoire
  - Si la valeur est true, le paramètre doit apparaître dans toutes les commandes qui utilisent le jeu de paramètres.
  - Si la valeur est false, le paramètre est facultatif dans toutes les commandes qui utilisent le jeu de paramètres.
- Position
  - S’il est nommé, le nom du paramètre est obligatoire.
  - Si positionnel, le nom du paramètre est facultatif. Lorsqu’elle est omise, la valeur du paramètre doit se trouver à la position spécifiée dans la commande. Par exemple, si la valeur est position = "1", la valeur du paramètre doit être la première ou la seule valeur de paramètre sans nom dans la commande.
- Entrée de pipeline
  - Si la valeur est true (ByValue), vous pouvez diriger l’entrée vers le paramètre. L’entrée est associée (« lié à ») au paramètre même si le nom de la propriété et le type d’objet ne correspondent pas au type attendu.
    Les composants de liaison de paramètres PowerShell essaient de convertir l’entrée dans le type correct et de faire échouer la commande uniquement lorsque le type ne peut pas être converti. Un seul paramètre d’un jeu de paramètres peut être associé à la valeur.
  - Si la valeur est true (ByPropertyName), vous pouvez diriger l’entrée vers le paramètre. Toutefois, l’entrée est associée au paramètre uniquement lorsque le nom du paramètre correspond au nom d’une propriété de l’objet d’entrée. Par exemple, si le nom du paramètre est `Path` , les objets transmis à l’applet de commande sont associés à ce paramètre uniquement lorsque l’objet a une propriété nommée Path.
  - Si la valeur est true (ByValue, ByPropertyName), vous pouvez diriger l’entrée vers le paramètre à l’aide d’un nom de propriété ou d’une valeur. Un seul paramètre d’un jeu de paramètres peut être associé à la valeur.
  - Si la valeur est false, vous ne pouvez pas diriger d’entrée vers ce paramètre.
- Globbing
  - Si la valeur est true, le texte que l’utilisateur tape pour la valeur de paramètre peut inclure des caractères génériques.
  - Si la valeur est false, le texte que l’utilisateur tape pour la valeur de paramètre ne peut pas inclure de caractères génériques.

### <a name="parameter-value-attributes"></a>Attributs de valeur de paramètre

- Obligatoire
  - Si la valeur est true, la valeur spécifiée doit être utilisée chaque fois que le paramètre est utilisé dans une commande.
  - Si la valeur est false, la valeur du paramètre est facultative. En règle générale, une valeur est facultative uniquement lorsqu’il s’agit de l’une des nombreuses valeurs valides pour un paramètre, par exemple dans un type énuméré.

L’attribut **requis** d’une valeur de paramètre est différent de l’attribut **requis** d’un paramètre.

L’attribut required d’un paramètre indique si le paramètre (et sa valeur) doit être inclus lors de l’appel de l’applet de commande. En revanche, l’attribut required d’une valeur de paramètre est utilisé uniquement lorsque le paramètre est inclus dans la commande. Elle indique si cette valeur particulière doit être utilisée avec le paramètre.

En règle générale, les valeurs de paramètre qui sont des espaces réservés sont obligatoires et les valeurs de paramètre qui sont des littéraux ne sont pas requises, car il s’agit de l’une des nombreuses valeurs qui peuvent être utilisées avec le paramètre.

### <a name="gathering-syntax-information"></a>Collecte d’informations de syntaxe

1. Commencez par le nom de l’applet de commande.

   ```
   SYNTAX
       Get-Tech
   ```

1. Répertorie tous les paramètres de l’applet de commande. Tapez un trait d’Union ( `-` ) (ASCII 45) avant chaque nom de paramètre.
   Séparez les paramètres en jeux de paramètres (certaines applets de commande ne peuvent avoir qu’un seul jeu de paramètres). Dans cet exemple, l’applet de commande Get-Tech a deux jeux de paramètres.

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   Démarrez chaque jeu de paramètres avec le nom de l’applet de commande.

   Répertoriez d’abord le jeu de paramètres par défaut. Le paramètre par défaut est spécifié par la classe cmdlet.

   Pour chaque jeu de paramètres, listez son paramètre unique en premier, sauf s’il existe des paramètres positionnels qui doivent apparaître en premier. Dans l’exemple précédent, les paramètres Name et ID sont des paramètres uniques pour les deux jeux de paramètres (chaque jeu de paramètres doit avoir un paramètre unique pour ce jeu de paramètres). Cela permet aux utilisateurs d’identifier plus facilement le paramètre qu’ils doivent fournir pour le jeu de paramètres.

   Répertoriez les paramètres dans l’ordre dans lequel ils doivent apparaître dans la commande. Si l’ordre n’a pas d’importance, listez les paramètres associés ou répertoriez d’abord les paramètres les plus fréquemment utilisés.

   Veillez à répertorier les paramètres WhatIf et Confirm si l’applet de commande prend en charge ShouldProcess.

   Ne répertoriez pas les paramètres communs (tels que verbose, Debug et ErrorAction) dans votre diagramme de syntaxe. L' `Get-Help` applet de commande ajoute ces informations lors de l’affichage de la rubrique d’aide.

1. Ajoutez les valeurs des paramètres. Dans PowerShell, les valeurs de paramètres sont représentées par leur type .NET.
   Toutefois, le nom de type peut être abrégé, par exemple « String » pour System. String.

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   Abrégez les types tant que leur signification est claire, telle que **String** pour **System. String** et **int** pour **System. Int32**.

   Répertorie toutes les valeurs des énumérations, telles que le `-type` paramètre dans l’exemple précédent, qui peut être défini sur de **base** ou **avancé**.

   Les paramètres de commutateur, comme `-list` dans l’exemple précédent, n’ont pas de valeurs.

1. Ajoutez des crochets pointus aux valeurs de paramètres qui sont des espaces réservés, par rapport aux valeurs de paramètres qui sont des littéraux.

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

1. Placez les paramètres facultatifs et leurs valeurs entre crochets.

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

1. Placez les noms de paramètres facultatifs (pour les paramètres positionnels) entre crochets. Le nom des paramètres qui sont positionnels, tels que le paramètre Name dans l’exemple suivant, n’a pas besoin d’être inclus dans la commande.

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

1. Si une valeur de paramètre peut contenir plusieurs valeurs, telles qu’une liste de noms dans le paramètre Name, ajoutez une paire de crochets directement après la valeur du paramètre.

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

1. Si l’utilisateur peut choisir parmi des paramètres ou des valeurs de paramètre, tels que le paramètre de type, mettez les choix entre accolades et séparez-les par le symbole OR exclusif (;).

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

1. Si la valeur du paramètre doit utiliser une mise en forme spécifique, telle que des guillemets ou des parenthèses, affichez le format dans la syntaxe.

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a>Codage du diagramme XML de la syntaxe

Le nœud de syntaxe du fichier XML commence immédiatement après le nœud Description, qui se termine par la `</maml:description>` balise. Pour plus d’informations sur la collecte des données utilisées dans le diagramme de syntaxe, consultez [collecte d’informations de syntaxe](#gathering-syntax-information).

### <a name="adding-a-syntax-node"></a>Ajout d’un nœud de syntaxe

Le diagramme de syntaxe affiché dans la rubrique d’aide de l’applet de commande est généré à partir des données du nœud de syntaxe du XML. Le nœud de syntaxe est placé entre deux `<command:syntax>` balises. Avec chaque jeu de paramètres de l’applet de commande placée dans une paire de `<command:syntaxitem>` balises. Il n’existe aucune limite au nombre de `<command:syntaxitem>` balises que vous pouvez ajouter.

L’exemple suivant montre un nœud de syntaxe qui possède des nœuds élément de syntaxe pour deux jeux de paramètres.

```xml
<command:syntax>
  <command:syntaxItem>
    ...
    <!--Parameter Set 1 (default parameter set) parameters go here-->
    ...
  </command:syntaxItem>
  <command:syntaxItem>
    ...
    <!--Parameter Set 2 parameters go here-->
    ...
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a>Ajout du nom de l’applet de commande aux données du jeu de paramètres

Chaque jeu de paramètres de l’applet de commande est spécifié dans un nœud élément de syntaxe. Chaque nœud d’élément de syntaxe commence par une paire de `<maml:name>` balises qui inclut le nom de l’applet de commande.

L’exemple suivant inclut un nœud de syntaxe qui possède des nœuds élément de syntaxe pour deux jeux de paramètres.

```xml
<command:syntax>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-parameters"></a>Ajouter des paramètres

Chaque paramètre ajouté au nœud élément de syntaxe est spécifié dans une paire de `<command:parameter>` balises. Vous avez besoin d’une paire de `<command:parameter>` balises pour chaque paramètre inclus dans le jeu de paramètres, à l’exception des paramètres communs fournis par PowerShell.

Les attributs de la `<command:parameter>` balise d’ouverture déterminent la façon dont le paramètre apparaît dans le diagramme de syntaxe. Pour plus d’informations sur les attributs de paramètres, consultez [attributs de paramètres](#parameter-attributes).

> [!NOTE]
> La `<command:parameter>` balise prend en charge un élément enfant `<maml:description>` dont le contenu n’est jamais affiché. Les descriptions des paramètres sont spécifiées dans le nœud du paramètre du XML. Pour éviter les incohérences entre les informations de l’élément de syntaxe Bodes et le nœud de paramètre, omettez le ( `<maml:description>` ou laissez-le vide.

L’exemple suivant comprend un nœud élément de syntaxe pour un jeu de paramètres avec deux paramètres.

```xml
<command:syntaxItem>
  <maml:name>Cmdlet-Name</maml:name>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByValue)" position="1">
    <maml:name>ParameterName1</maml:name>
    <command:parameterValue required="true">
      string[]
    </command:parameterValue>
  </command:parameter>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByPropertyName)">
    <maml:name>ParameterName2</maml:name>
    <command:parameterValue required="true">
      int32[]
    </command:parameterValue>
  </command:parameter>
</command:syntaxItem>
```
