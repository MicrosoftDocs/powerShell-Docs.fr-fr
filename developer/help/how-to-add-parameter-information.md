---
title: Comment ajouter des informations sur les paramètres | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf6c1442-60aa-477a-8f30-ab02b1b11039
caps.latest.revision: 7
ms.openlocfilehash: d4a5fc934a41b00f89862674e44e4540680674f7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083363"
---
# <a name="how-to-add-parameter-information"></a>Guide pratique pour ajouter des informations sur les paramètres

Cette section décrit comment ajouter du contenu qui s’affiche dans la section Paramètres de rubrique d’aide de l’applet de commande. La section Paramètres de la rubrique d’aide répertorie chacun des paramètres de l’applet de commande et fournit une description détaillée de chaque paramètre.

Le contenu de la section de paramètres doit être cohérent avec le contenu de la section syntaxe de la rubrique d’aide. Il incombe à l’auteur de l’aide pour vous assurer que la syntaxe et les paramètres de nœud contiennent des éléments XML.

> [!NOTE]
> Pour obtenir une vue complète d’un fichier d’aide, ouvrez un des fichiers dll-Help.xml situé dans le répertoire d’installation de Windows PowerShell. Par exemple, le fichier Microsoft.PowerShell.Commands.Management.dll-Help.xml contient le contenu pour plusieurs des applets de commande Windows PowerShell.

### <a name="to-add-parameters"></a>Pour ajouter des paramètres

1. Ouvrez le fichier d’aide de l’applet de commande et recherchez le nœud de commande pour l’applet de commande que vous décrivez. Si vous ajoutez une nouvelle applet de commande, vous devrez créer un nouveau nœud de commande. Votre fichier d’aide contient un nœud de commande pour chaque applet de commande que vous fournissez du contenu d’aide pour. Voici un exemple d’un nœud vide de la commande.

    ```xml
    <command:command>
    </command:command>
    ```

2. Dans le nœud de la commande, recherchez le nœud de Description et ajouter un nœud de paramètres comme indiqué ci-dessous. Qu’un seul nœud de paramètres est autorisé, et elle doit suivre immédiatement le nœud de syntaxe.

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. Dans le nœud Paramètres, ajoutez un nœud de paramètre pour chaque paramètre de l’applet de commande, comme indiqué ci-dessous.

   Dans cet exemple, un nœud de paramètre est ajouté pour trois paramètres.

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   Puisque ce sont les mêmes balises XML qui sont utilisées dans le nœud de syntaxe et étant donné que les paramètres spécifiés ici doivent correspondre à des paramètres spécifiés par le nœud de syntaxe, vous pouvez copier les nœuds de paramètre à partir du nœud de syntaxe et les coller dans le nœud Paramètres. Toutefois, veillez à ne copier qu’une seule instance d’un nœud de paramètre, même si le paramètre est spécifié dans plusieurs jeux de paramètres dans la syntaxe.

4. Pour chaque nœud de paramètre, définissez les valeurs d’attribut qui définissent les caractéristiques de chaque paramètre. Ces attributs sont les suivants : obligatoire, l’utilisation des caractères génériques, pipelineinput et la position.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named" ></command:parameter>
    </command:Parameters>
    ```

5. Pour chaque nœud de paramètre, ajoutez le nom du paramètre. Voici un exemple du nom du paramètre ajouté au nœud de paramètre.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. Pour chaque nœud de paramètre, ajoutez la description du paramètre. Voici un exemple de la description du paramètre ajouté au nœud de paramètre.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
      </command:parameter>
    </command:parameters>
    ```

7. Pour chaque nœud de paramètre, ajoutez le paramètre de type .NET Framework. Le type de paramètre s’affiche avec le nom du paramètre.

   Voici un exemple du type .NET Framework paramètre ajouté au nœud de paramètre.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
      </command:parameter>
    </command:parameters>
    ```

8. Pour chaque nœud de paramètre, ajoutez la valeur par défaut du paramètre. La phrase suivante est ajoutée à la description du paramètre lorsque le contenu est affiché : « DefaultValue » est la valeur par défaut.

   Voici un exemple de la valeur par défaut du paramètre est ajouté au nœud de paramètre.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
        <dev:defaultvalue> Add default value...</dev:defaultvalue>
      </command:parameter>
    </command:parameters>
    ```

9. Pour chaque paramètre qui a plusieurs valeurs, ajoutez un nœud de valeurs possibles.

   Voici un exemple de la d’un nœud de valeurs possibles qui définit deux valeurs possibles pour le paramètre

    ```xml
    <dev:possiblevalues>
      <dev:possiblevalue>
        <dev:value>Unknown</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      /dev:possiblevalue>
      <dev:possiblevalue>
        <dev:value>String</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possibleValue>
    </dev:possiblevalues>
    ```

Voici quelques points à retenir lors de l’ajout de paramètres.

- Les attributs du paramètre ne sont pas affichés dans toutes les vues de la rubrique d’aide de l’applet de commande. Toutefois, ils sont affichés dans une table suivant la description du paramètre lorsque l’utilisateur demande pour la version complète (Get-Help \<cmdletname >-complet) ou un paramètre (Get-Help \<cmdletname >-paramètre) Affichage de la rubrique.

- La description du paramètre est une des parties plus importantes d’une rubrique d’aide applet de commande. La description doit être brève, mais aussi approfondie. En outre, n’oubliez pas que si la description du paramètre devient trop longue, par exemple lorsque les deux paramètres interagissent entre eux, vous pouvez ajouter davantage de contenu dans la section Remarques de la rubrique d’aide de l’applet de commande.

  La description du paramètre fournit deux types d’informations.

- Ce que l’applet de commande fait lorsque le paramètre est utilisé.

- Quelles une valeur autorisée est pour le paramètre.

- Étant donné que les valeurs de paramètre sont exprimées en tant qu’objets .NET Framework, les utilisateurs ont besoin de plus d’informations sur ces valeurs qu’elles le feraient dans une aide en ligne de commande traditionnelle. Indiquer à quel type de données, le paramètre est conçu pour accepter l’utilisateur et incluent des exemples.

La valeur par défaut du paramètre est la valeur qui est utilisée si le paramètre n’est pas spécifié sur la ligne de commande. Notez que la valeur par défaut est facultative et n’est pas nécessaire pour certains paramètres, tels que les paramètres requis. Toutefois, vous devez spécifier une valeur par défaut pour la plupart des paramètres facultatifs.

La valeur par défaut aide l’utilisateur à comprendre l’effet de ne pas utiliser le paramètre. Décrire la valeur par défaut d’une manière très spécifique, tel que le « répertoire actif » ou « Windows PowerShell répertoire d’installation ($pshome) » pour un chemin d’accès facultatif. Vous pouvez également écrire une phrase qui décrit la valeur par défaut, telles que la phrase suivante est utilisée pour le `PassThru` paramètre : « Si PassThru n’est pas spécifié, l’applet de commande ne transmet pas les objets dans le pipeline. »  En outre, étant donné que la valeur est affichée en regard du nom du champ «**valeur par défaut**», vous n’avez pas besoin d’inclure le terme « default value » dans l’entrée.

La valeur par défaut du paramètre n’est pas affichée dans toutes les vues de la rubrique d’aide de l’applet de commande. Toutefois, il est affiché dans une table (ainsi que les attributs de paramètre) en suivant la description du paramètre lorsque l’utilisateur demande pour la version complète (Get-Help \<cmdletname >-complet) ou un paramètre (Get-Help \<cmdletname >-paramètre) vue de la rubrique.

Le code XML suivant montre une paire de `<dev:defaultValue>` balises ajoutées à la `<command:parameter>` nœud. Notez que la valeur par défaut suit immédiatement après la fermeture `</command:parameterValue>` balise (lorsque la valeur du paramètre est spécifiée) ou la fermeture `</maml:description>` balise de la description du paramètre. Nom.

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
  </command:parameter>
</command:parameters>
```

Ajoutez des valeurs pour les Types énumérés

Si le paramètre a plusieurs valeurs ou les valeurs d’un type énuméré, vous pouvez utiliser un texte facultatif \<dev:possibleValues > nœud. Ce nœud vous permet de spécifier un nom et une description pour les valeurs multiples.

N’oubliez pas que les descriptions des valeurs énumérées n’apparaissent pas dans un de la valeur par défaut aide les vues affichées par le `Get-Help` applet de commande, mais les autres visionneuses aide peuvent afficher ce contenu dans leurs vues.

Le code XML suivant montre un `<dev:possibleValues>` nœud avec deux valeurs spécifiées.

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
    <dev:possibleValues>
      <dev:possibleValue>
        <dev:value> Value 1 </dev:value>
        <maml:description>
          <maml:para> Description 1 </maml:para>
        </maml:description>
      <dev:possibleValue>
      <dev:possibleValue>
        <dev:value> Value 2 </dev:value>
        <maml:description>
          <maml:para> Description 2 </maml:para>
        </maml:description>
      <dev:possibleValue>
    </dev:possibleValues>
  </command:parameter>
</command:parameters>
```