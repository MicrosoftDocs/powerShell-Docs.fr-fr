---
title: Comment ajouter la syntaxe pour une rubrique d’aide applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0c6d03f-1c1a-43d8-928e-e3290e90e0bc
caps.latest.revision: 5
ms.openlocfilehash: 2e9dbc9ff8f9507f2008cd6e114ba6fec36b10bf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083380"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a>Guide pratique pour ajouter la syntaxe à une rubrique d’aide d’applet de commande

- [Attributs de paramètre](#Parameter-Attributes)

- [Attributs de valeur de paramètre](#Parameter-Value-Attributes)

- [Collecte des informations sur la syntaxe](#Gathering-Syntax-Information)

- [Le diagramme de syntaxe XML de codage](#Coding-the-Syntax-Diagram-XML)

## <a name="things-to-know-about-the-syntax-diagram-in-cmdlet-help"></a>Choses à savoir sur le diagramme de syntaxe dans l’aide de l’applet de commande

Avant de commencer à coder le code XML pour le diagramme de syntaxe dans le fichier d’aide applet de commande, lisez cette section pour obtenir une vision claire du type de données, que vous devez fournir, telles que les attributs de paramètre et le mode d’affichage de ces données dans le diagramme de syntaxe...

### <a name="parameter-attributes"></a>Attributs de paramètre

- Obligatoire

  - Si la valeur est true, le paramètre doit apparaître dans toutes les commandes qui utilisent le jeu de paramètres.

  - Si la valeur est false, le paramètre est facultatif dans toutes les commandes qui utilisent le jeu de paramètres.

- Position

  - Si nommée, le nom de paramètre est obligatoire.

  - Si la position, le nom de paramètre est facultatif. Lorsqu’il est omis, la valeur du paramètre doit être dans la position spécifiée dans la commande. Par exemple, si la valeur est la position = « 1 », la valeur du paramètre doit être la première ou la seule valeur de paramètre dans la commande sans nom.

- Entrée de pipeline

  - Si la valeur est true (ByValue), vous pouvez rediriger l’entrée pour le paramètre. L’entrée est associée avec (« limite à ») le paramètre même si le nom de propriété et le type d’objet ne correspondent pas au type attendu. La commande Windows PowerShell ? composants de liaison de paramètre essayez de convertir l’entrée en type correct et de faire échouer la commande uniquement lorsque le type ne peut pas être converti. Qu’un seul paramètre dans un jeu de paramètres peut être associé par valeur.

  - Si la valeur est true (ByPropertyName), vous pouvez rediriger l’entrée pour le paramètre. Toutefois, l’entrée est associée au paramètre uniquement lorsque le nom du paramètre correspond au nom d’une propriété de l’objet d’entrée. Par exemple, si le nom du paramètre est `Path`, objets dirigés vers l’applet de commande sont associés à ce paramètre uniquement lorsque l’objet a une propriété nommée du chemin d’accès.

  - Si la valeur true (ByValue, ByPropertyName), vous pouvez rediriger l’entrée pour le paramètre par nom ou par valeur. Qu’un seul paramètre dans un jeu de paramètres peut être associé par valeur.

  - Si la valeur est false, vous ne pouvez pas diriger d’entrée pour ce paramètre.

- Utilisation des caractères génériques

  - Si la valeur est true, le texte que l’utilisateur tape pour la valeur du paramètre peut inclure des caractères génériques.

  - Si la valeur est false, le texte que l’utilisateur tape pour la valeur du paramètre ne peut pas inclure des caractères génériques.

### <a name="parameter-value-attributes"></a>Attributs de valeur de paramètre

- Obligatoire

  - Si la valeur est true, la valeur spécifiée doit être utilisée chaque fois que l’utilisation du paramètre dans une commande.

  - Si la valeur est false, la valeur du paramètre est facultative. En règle générale, une valeur est facultative uniquement lorsqu’il est une de plusieurs valeurs valides pour un paramètre, comme dans un type énuméré.

L’attribut requis d’une valeur de paramètre est différent de l’attribut d’un paramètre requis.

L’attribut requis d’un paramètre indique si le paramètre (et sa valeur) doivent être incluses lors de l’appel de l’applet de commande. En revanche, l’attribut requis d’une valeur de paramètre est utilisé uniquement lorsque le paramètre est inclus dans la commande. Cette propriété indique si cette valeur doit être utilisée avec le paramètre.

En règle générale, les valeurs de paramètre qui sont des espaces réservés sont requis et les valeurs de paramètre sont littéral ne sont pas requis, car elles sont une des valeurs suivantes qui peuvent être utilisées avec le paramètre.

### <a name="gathering-syntax-information"></a>Collecte des informations sur la syntaxe

1. Démarrer avec le nom de l’applet de commande.

   ```
   SYNTAX
       Get-Tech
   ```

2. Liste de tous les paramètres de l’applet de commande. Tapez un tiret (également appelée « dash » ou « signe » (ASCII 45) devant chaque nom de paramètre. Séparez les paramètres dans les jeux de paramètres (certaines applets de commande peut avoir qu’un seul paramètre défini). Dans cet exemple le Get-Tech applet de commande a deux jeux de paramètres.

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   Chaque paramètre défini avec le nom de l’applet de commande de démarrage.

   Le paramètre par défaut défini au préalable de la liste. Le paramètre par défaut est spécifié par la classe de l’applet de commande.

   Pour chaque jeu de paramètres, indiquez son paramètre unique tout d’abord, sauf s’il existe des paramètres positionnels qui doivent apparaître en premier. Dans l’exemple précédent, les paramètres de nom et l’ID sont des paramètres uniques pour les deux jeux de paramètres (chaque jeu de paramètres doit avoir un seul paramètre qui est unique pour ce jeu de paramètres). Cela rend plus facile pour les utilisateurs à identifier quel paramètre dont ils ont besoin pour fournir pour le paramètre défini.

   Répertorier les paramètres dans l’ordre où ils doivent apparaître dans la commande. Si l’ordre n’a pas d’importance, regrouper les paramètres associés, ou indiquez tout d’abord les paramètres fréquemment utilisés.

   Veillez à répertorier les paramètres WhatIf et Confirm si l’applet de commande prend en charge ShouldProcess.

   Ne répertorient pas les paramètres communs (tels que Verbose, Debug et ErrorAction) dans votre diagramme de syntaxe. Le `Get-Help` applet de commande ajoute ces informations pour vous lors de l’affichage de la rubrique d’aide.

3. Ajoutez les valeurs de paramètre. Dans Windows PowerShell ?, les valeurs de paramètre sont représentées par leur type .NET. Toutefois, le nom de type peut être abrégé, tel que « string » pour System.String.

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   Abréger types tant que leur signification est claire, tels que « string » pour System.String et « int » pour System.Int32.

   Liste de toutes les valeurs des énumérations, telles que le paramètre - type dans l’exemple précédent, ce qui peut être défini sur « basic » ou « advanced ».

   Passer des paramètres, tels que - liste dans l’exemple précédent, n’ont pas de valeurs.

4. Ajouter les crochets pointus aux valeurs de paramètres qui sont l’espace réservé, par rapport aux valeurs de paramètre qui sont des littéraux.

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. Entrez les paramètres facultatifs et leurs valeurs de crochets.

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. Placez les noms de paramètres facultatifs (pour les paramètres positionnels) entre crochets. Le nom pour les paramètres positionnels, tels que le paramètre de nom dans l’exemple suivant, n’ont pas à être inclus dans la commande.

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. Si une valeur de paramètre peut contenir plusieurs valeurs, telles qu’une liste de noms dans le paramètre Name, ajoutez une paire de crochets directement après la valeur du paramètre.

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. Si l’utilisateur peut choisir à partir des paramètres ou des valeurs de paramètre, tels que le paramètre de Type, placez les choix entre accolades, en les séparant avec le symbol(;) OR exclusif.

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. Si la valeur du paramètre doit utiliser une mise en forme spécifiques, tels que des guillemets ou des parenthèses, montrent le format dans la syntaxe.

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a>Le diagramme de syntaxe XML de codage

Le nœud de syntaxe du code XML commence immédiatement après le nœud de description, qui se termine par le \</maml:description > balise. Pour plus d’informations sur la collecte des données utilisées dans le diagramme de syntaxe, consultez [collecte des informations sur la syntaxe](#Gathering-Syntax-Information).

### <a name="adding-a-syntax-node"></a>Ajout d’un nœud de syntaxe

Le diagramme de syntaxe affiché dans la rubrique d’aide de l’applet de commande est généré à partir des données dans le nœud de syntaxe du document XML. Le nœud de syntaxe est placé dans une paire si \<: syntaxe de commande > balises. Avec chaque jeu de paramètres de l’applet de commande placé dans une paire de \<commande : syntaxitem > balises. Il n’existe aucune limite au nombre de \<commande : syntaxitem > balises que vous pouvez ajouter.

L’exemple suivant montre un nœud de syntaxe qui possède des nœuds d’élément de syntaxe pour les deux jeux de paramètres.

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

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a>Ajout du nom de l’applet de commande au paramètre définie les données

Chaque jeu de paramètres de l’applet de commande est spécifié dans un nœud d’élément de syntaxe. Chaque nœud d’élément de syntaxe commence par une paire de \<maml:name > balises qui incluent le nom de l’applet de commande.

L’exemple suivant inclut un nœud de syntaxe qui possède des nœuds d’élément de syntaxe pour les deux jeux de paramètres.

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

### <a name="adding-parameters"></a>Ajout de paramètres

Chaque paramètre est ajouté au nœud d’élément de syntaxe est spécifiée au sein d’une paire de \<: paramètre de commande > balises. Vous avez besoin d’une paire de \<: paramètre de commande > balises pour chaque paramètre inclus dans le jeu de paramètres, à l’exception des paramètres courants que sont fournies par Windows PowerShell ?.

Les attributs de l’ouverture \<: paramètre de commande > balise déterminer comment le paramètre apparaît dans le diagramme de syntaxe. Pour plus d’informations sur les attributs de paramètre, consultez [les attributs de paramètre](#Parameter-Attributes).

> [!NOTE]
> Le \<: paramètre de commande > balise prend en charge un élément enfant \<maml:description > dont le contenu n’est jamais affiché. Les descriptions de paramètre sont spécifiées dans le nœud de paramètre du fichier XML. Pour éviter les incohérences entre les informations contenues dans l’élément de syntaxe plan et le nœud de paramètre, omettez la (\<maml:description > ou laissez-le vide.

L’exemple suivant inclut un nœud d’élément de syntaxe pour un paramètre défini avec deux paramètres.

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
