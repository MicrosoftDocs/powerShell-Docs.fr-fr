---
title: Guide pratique pour ajouter des informations sur les paramètres
ms.date: 09/12/2016
ms.openlocfilehash: 15d0194a1d5449c65977703faf245e449d75d176
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893388"
---
# <a name="how-to-add-parameter-information"></a>Guide pratique pour ajouter des informations sur les paramètres

Cette section décrit comment ajouter du contenu qui s’affiche dans la section **paramètres** de la rubrique d’aide de l’applet de commande. La section **paramètres** de la rubrique d’aide répertorie chacun des paramètres de l’applet de commande et fournit une description détaillée de chaque paramètre.

Le contenu de la section des **paramètres** doit être cohérent avec le contenu de la section **syntaxe** de la rubrique d’aide. Il incombe à l’auteur de l’aide de s’assurer que le nœud de **syntaxe** et de **paramètres** contient des éléments XML similaires.

> [!NOTE]
> Pour obtenir une vue complète d’un fichier d’aide, ouvrez l’un des `dll-Help.xml` fichiers situés dans le répertoire d’installation de PowerShell. Par exemple, le `Microsoft.PowerShell.Commands.Management.dll-Help.xml` fichier contient du contenu pour plusieurs des applets de commande PowerShell.

### <a name="to-add-parameters"></a>Pour ajouter des paramètres

1. Ouvrez le fichier d’aide de l’applet de commande et recherchez le nœud de commande pour l’applet de commande que vous documentez. Si vous ajoutez une nouvelle applet de commande, vous devez créer un nouveau nœud de commande. Votre fichier d’aide contiendra un nœud de commande pour chaque cmdlet pour laquelle vous fournissez du contenu d’aide. Voici un exemple de nœud de commande vide.

    ```xml
    <command:command>
    </command:command>
    ```

1. Dans le nœud de commande, localisez le nœud Description et ajoutez un nœud paramètres comme indiqué ci-dessous.
   Un seul nœud de paramètres est autorisé et il doit suivre immédiatement le nœud de syntaxe.

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

1. Dans le nœud Paramètres, ajoutez un nœud de **paramètre** pour chaque paramètre de l’applet de commande, comme indiqué ci-dessous.

   Dans cet exemple, un nœud de **paramètre** est ajouté pour trois paramètres.

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   Étant donné que ces balises XML sont les mêmes que celles utilisées dans le nœud de syntaxe et que les paramètres spécifiés ici doivent correspondre aux paramètres spécifiés par le nœud de syntaxe, vous pouvez copier les nœuds de paramètres à partir du nœud de syntaxe et les coller dans le nœud Paramètres. Toutefois, veillez à ne copier qu’une seule instance d’un nœud de paramètre, même si le paramètre est spécifié dans plusieurs jeux de paramètres dans la syntaxe.

1. Pour chaque nœud de paramètre, définissez les valeurs d’attribut qui définissent les caractéristiques de chaque paramètre. Ces attributs sont les suivants : required, globbing, PipelineInput et position.

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

1. Pour chaque nœud de paramètre, ajoutez le nom du paramètre. Voici un exemple de nom de paramètre ajouté au nœud de paramètre.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

1. Pour chaque nœud de **paramètre** , ajoutez la description du paramètre. Voici un exemple de la description de paramètre ajoutée au nœud de **paramètre** .

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

1. Pour chaque nœud de **paramètre** , ajoutez le type .net du paramètre. Le type de paramètre est affiché avec le nom du paramètre.

   Voici un exemple de type .NET de paramètre ajouté au nœud de **paramètre** .

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

1. Pour chaque nœud de **paramètre** , ajoutez la valeur par défaut du paramètre. La phrase suivante est ajoutée à la description du paramètre lorsque le contenu est affiché : **DefaultValue** est la valeur par défaut.

   Voici un exemple de la valeur par défaut du paramètre est ajouté au nœud du **paramètre** .

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

1. Pour chaque paramètre ayant plusieurs valeurs, ajoutez un nœud valeurs possibles.

   Voici un exemple de l’un des nœuds de valeurs possibles qui définit deux valeurs possibles pour le paramètre.

    ```xml
    <dev:possiblevalues>
      <dev:possiblevalue>
        <dev:value>Unknown</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possiblevalue>
      <dev:possiblevalue>
        <dev:value>String</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possibleValue>
    </dev:possiblevalues>
    ```

Voici quelques points à retenir lors de l’ajout de paramètres.

- Les attributs du paramètre ne sont pas affichés dans toutes les vues de la rubrique d’aide de l’applet de commande. Toutefois, ils sont affichés dans un tableau qui suit la description du paramètre lorsque l’utilisateur demande la vue **complète** ( `Get-Help <cmdletname> -full` ) ou du **paramètre** ( `Get-Help <cmdletname> -parameter` ) de la rubrique.

- La description du paramètre est l’une des parties les plus importantes d’une rubrique d’aide sur une applet de commande. La description doit être brève, ainsi que minutieusement. En outre, n’oubliez pas que si la description du paramètre devient trop longue, par exemple quand deux paramètres interagissent entre eux, vous pouvez ajouter du contenu dans la section Remarques de la rubrique d’aide de l’applet de commande.

  La description du paramètre fournit deux types d’informations.

- Ce que fait l’applet de commande lorsque le paramètre est utilisé.

- Ce qu’est une valeur légale pour le paramètre.

- Étant donné que les valeurs des paramètres sont exprimées en tant qu’objets .NET, les utilisateurs ont besoin de plus d’informations sur ces valeurs que dans une aide de ligne de commande classique. Indiquez à l’utilisateur le type de données que le paramètre est destiné à accepter et incluez des exemples.

La valeur par défaut du paramètre est la valeur utilisée si le paramètre n’est pas spécifié sur la ligne de commande. Notez que la valeur par défaut est facultative et n’est pas nécessaire pour certains paramètres, tels que les paramètres requis. Toutefois, vous devez spécifier une valeur par défaut pour la plupart des paramètres facultatifs.

La valeur par défaut permet à l’utilisateur de comprendre l’effet de ne pas utiliser le paramètre. Décrivez la valeur par défaut de manière très spécifique, par exemple le « répertoire actif » ou le « répertoire d’installation PowerShell ( `$PSHOME` ) » pour un chemin d’accès facultatif. Vous pouvez également écrire une phrase qui décrit la valeur par défaut, telle que la phrase suivante utilisée pour le paramètre **PassThru** : « si PassThru n’est pas spécifié, l’applet de commande ne passe pas d’objets dans le pipeline ». En outre, étant donné que la valeur est affichée en regard de la **valeur par défaut**du nom de champ, vous n’avez pas besoin d’inclure le terme « valeur par défaut » dans l’entrée.

La valeur par défaut du paramètre n’est pas affichée dans toutes les vues de la rubrique d’aide de l’applet de commande. Toutefois, il est affiché dans une table (avec les attributs de paramètre) qui suit la description du paramètre lorsque l’utilisateur demande la vue **complète** ( `Get-Help <cmdletname> -full` ) ou de **paramètre** ( `Get-Help
<cmdletname> -parameter` ) de la rubrique.

Le code XML suivant montre une paire de `<dev:defaultValue>` balises ajoutées au `<command:parameter>` nœud.
Notez que la valeur par défaut suit immédiatement après la `</command:parameterValue>` balise de fermeture (lorsque la valeur du paramètre est spécifiée) ou la `</maml:description>` balise de fermeture de la description du paramètre. nom.

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

Ajouter des valeurs pour les types énumérés

Si le paramètre a plusieurs valeurs ou valeurs d’un type énuméré, vous pouvez utiliser un nœud facultatif \<dev:possibleValues> . Ce nœud vous permet de spécifier un nom et une description pour plusieurs valeurs.

Sachez que les descriptions des valeurs énumérées n’apparaissent pas dans les vues d’aide par défaut affichées par l’applet de commande `Get-Help` , mais d’autres observateurs d’aide peuvent afficher ce contenu dans leurs vues.

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
