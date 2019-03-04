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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863325"
---
# <a name="how-to-add-parameter-information"></a><span data-ttu-id="c1f10-102">Guide pratique pour ajouter des informations sur les paramètres</span><span class="sxs-lookup"><span data-stu-id="c1f10-102">How to Add Parameter Information</span></span>

<span data-ttu-id="c1f10-103">Cette section décrit comment ajouter du contenu qui s’affiche dans la section Paramètres de rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c1f10-103">This section describes how to add content that is displayed in the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="c1f10-104">La section Paramètres de la rubrique d’aide répertorie chacun des paramètres de l’applet de commande et fournit une description détaillée de chaque paramètre.</span><span class="sxs-lookup"><span data-stu-id="c1f10-104">The PARAMETERS section of the Help topic lists each of the parameters of the cmdlet and provides a detailed description of each parameter.</span></span>

<span data-ttu-id="c1f10-105">Le contenu de la section de paramètres doit être cohérent avec le contenu de la section syntaxe de la rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="c1f10-105">The content of the PARAMETERS section should be consistent with the content of the SYNTAX section of the Help topic.</span></span> <span data-ttu-id="c1f10-106">Il incombe à l’auteur de l’aide pour vous assurer que la syntaxe et les paramètres de nœud contiennent des éléments XML.</span><span class="sxs-lookup"><span data-stu-id="c1f10-106">It is the responsibility of the Help author to make sure that both the Syntax and Parameters node contain similar XML elements.</span></span>

> [!NOTE]
> <span data-ttu-id="c1f10-107">Pour obtenir une vue complète d’un fichier d’aide, ouvrez un des fichiers dll-Help.xml situé dans le répertoire d’installation de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c1f10-107">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="c1f10-108">Par exemple, le fichier Microsoft.PowerShell.Commands.Management.dll-Help.xml contient le contenu pour plusieurs des applets de commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c1f10-108">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-parameters"></a><span data-ttu-id="c1f10-109">Pour ajouter des paramètres</span><span class="sxs-lookup"><span data-stu-id="c1f10-109">To Add Parameters</span></span>

1. <span data-ttu-id="c1f10-110">Ouvrez le fichier d’aide de l’applet de commande et recherchez le nœud de commande pour l’applet de commande que vous décrivez.</span><span class="sxs-lookup"><span data-stu-id="c1f10-110">Open the cmdlet Help file and locate the Command node for the cmdlet you are documenting.</span></span> <span data-ttu-id="c1f10-111">Si vous ajoutez une nouvelle applet de commande, vous devrez créer un nouveau nœud de commande.</span><span class="sxs-lookup"><span data-stu-id="c1f10-111">If you are adding a new cmdlet you will need to create a new Command node.</span></span> <span data-ttu-id="c1f10-112">Votre fichier d’aide contient un nœud de commande pour chaque applet de commande que vous fournissez du contenu d’aide pour.</span><span class="sxs-lookup"><span data-stu-id="c1f10-112">Your Help file will contain a Command node for each cmdlet that you are providing Help content for.</span></span> <span data-ttu-id="c1f10-113">Voici un exemple d’un nœud vide de la commande.</span><span class="sxs-lookup"><span data-stu-id="c1f10-113">Here is an example of a blank Command node.</span></span>

    ```xml
    <command:command>
    </command:command>
    ```

2. <span data-ttu-id="c1f10-114">Dans le nœud de la commande, recherchez le nœud de Description et ajouter un nœud de paramètres comme indiqué ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="c1f10-114">Within the Command node, locate the Description node and add a Parameters node as shown below.</span></span> <span data-ttu-id="c1f10-115">Qu’un seul nœud de paramètres est autorisé, et elle doit suivre immédiatement le nœud de syntaxe.</span><span class="sxs-lookup"><span data-stu-id="c1f10-115">Only one Parameters node is allowed, and it should immediately follow the Syntax node.</span></span>

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. <span data-ttu-id="c1f10-116">Dans le nœud Paramètres, ajoutez un nœud de paramètre pour chaque paramètre de l’applet de commande, comme indiqué ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="c1f10-116">Within the Parameters node, add a Parameter node for each parameter of the cmdlet as shown below.</span></span>

   <span data-ttu-id="c1f10-117">Dans cet exemple, un nœud de paramètre est ajouté pour trois paramètres.</span><span class="sxs-lookup"><span data-stu-id="c1f10-117">In this example, a Parameter node is added for three parameters.</span></span>

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   <span data-ttu-id="c1f10-118">Puisque ce sont les mêmes balises XML qui sont utilisées dans le nœud de syntaxe et étant donné que les paramètres spécifiés ici doivent correspondre à des paramètres spécifiés par le nœud de syntaxe, vous pouvez copier les nœuds de paramètre à partir du nœud de syntaxe et les coller dans le nœud Paramètres.</span><span class="sxs-lookup"><span data-stu-id="c1f10-118">Because these are the same XML tags that are used in the Syntax node, and because the parameters specified here must match the parameters specified by the Syntax node, you can copy the Parameter nodes from the Syntax node and paste them into the Parameters node.</span></span> <span data-ttu-id="c1f10-119">Toutefois, veillez à ne copier qu’une seule instance d’un nœud de paramètre, même si le paramètre est spécifié dans plusieurs jeux de paramètres dans la syntaxe.</span><span class="sxs-lookup"><span data-stu-id="c1f10-119">However, be sure to copy only one instance of a Parameter node, even if the parameter is specified in multiple parameter sets in the syntax.</span></span>

4. <span data-ttu-id="c1f10-120">Pour chaque nœud de paramètre, définissez les valeurs d’attribut qui définissent les caractéristiques de chaque paramètre.</span><span class="sxs-lookup"><span data-stu-id="c1f10-120">For each Parameter node, set the attribute values that define the characteristics of each parameter.</span></span> <span data-ttu-id="c1f10-121">Ces attributs sont les suivants : obligatoire, l’utilisation des caractères génériques, pipelineinput et la position.</span><span class="sxs-lookup"><span data-stu-id="c1f10-121">These attributes include the following: required, globbing, pipelineinput, and position.</span></span>

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

5. <span data-ttu-id="c1f10-122">Pour chaque nœud de paramètre, ajoutez le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="c1f10-122">For each Parameter node, add the name of the parameter.</span></span> <span data-ttu-id="c1f10-123">Voici un exemple du nom du paramètre ajouté au nœud de paramètre.</span><span class="sxs-lookup"><span data-stu-id="c1f10-123">Here is an example of the parameter name added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. <span data-ttu-id="c1f10-124">Pour chaque nœud de paramètre, ajoutez la description du paramètre.</span><span class="sxs-lookup"><span data-stu-id="c1f10-124">For each Parameter node, add the description of the parameter.</span></span> <span data-ttu-id="c1f10-125">Voici un exemple de la description du paramètre ajouté au nœud de paramètre.</span><span class="sxs-lookup"><span data-stu-id="c1f10-125">Here is an example of the parameter description added to the Parameter node.</span></span>

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

7. <span data-ttu-id="c1f10-126">Pour chaque nœud de paramètre, ajoutez le paramètre de type .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c1f10-126">For each Parameter node, add the .NET Framework type of the parameter.</span></span> <span data-ttu-id="c1f10-127">Le type de paramètre s’affiche avec le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="c1f10-127">The parameter type is displayed along with the parameter name.</span></span>

   <span data-ttu-id="c1f10-128">Voici un exemple du type .NET Framework paramètre ajouté au nœud de paramètre.</span><span class="sxs-lookup"><span data-stu-id="c1f10-128">Here is an example of the parameter .NET Framework type added to the Parameter node.</span></span>

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

8. <span data-ttu-id="c1f10-129">Pour chaque nœud de paramètre, ajoutez la valeur par défaut du paramètre.</span><span class="sxs-lookup"><span data-stu-id="c1f10-129">For each Parameter node, add the default value of the parameter.</span></span> <span data-ttu-id="c1f10-130">La phrase suivante est ajoutée à la description du paramètre lorsque le contenu est affiché : « DefaultValue » est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="c1f10-130">The following sentence is added to the parameter description when the content is displayed: "DefaultValue" is the default.</span></span>

   <span data-ttu-id="c1f10-131">Voici un exemple de la valeur par défaut du paramètre est ajouté au nœud de paramètre.</span><span class="sxs-lookup"><span data-stu-id="c1f10-131">Here is an example of the parameter default value is added to the Parameter node.</span></span>

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

9. <span data-ttu-id="c1f10-132">Pour chaque paramètre qui a plusieurs valeurs, ajoutez un nœud de valeurs possibles.</span><span class="sxs-lookup"><span data-stu-id="c1f10-132">For each Parameter that has multiple values, add a possible values node.</span></span>

   <span data-ttu-id="c1f10-133">Voici un exemple de la d’un nœud de valeurs possibles qui définit deux valeurs possibles pour le paramètre</span><span class="sxs-lookup"><span data-stu-id="c1f10-133">Here is an example of the of a possible values node that defines two possible values for the parameter</span></span>

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

<span data-ttu-id="c1f10-134">Voici quelques points à retenir lors de l’ajout de paramètres.</span><span class="sxs-lookup"><span data-stu-id="c1f10-134">Here are some things to remember when adding parameters.</span></span>

- <span data-ttu-id="c1f10-135">Les attributs du paramètre ne sont pas affichés dans toutes les vues de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c1f10-135">The attributes of the parameter are not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="c1f10-136">Toutefois, ils sont affichés dans une table suivant la description du paramètre lorsque l’utilisateur demande pour la version complète (Get-Help \<cmdletname >-complet) ou un paramètre (Get-Help \<cmdletname >-paramètre) Affichage de la rubrique.</span><span class="sxs-lookup"><span data-stu-id="c1f10-136">However, they are displayed in a table following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

- <span data-ttu-id="c1f10-137">La description du paramètre est une des parties plus importantes d’une rubrique d’aide applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c1f10-137">The parameter description is one of the most important parts of a cmdlet Help topic.</span></span> <span data-ttu-id="c1f10-138">La description doit être brève, mais aussi approfondie.</span><span class="sxs-lookup"><span data-stu-id="c1f10-138">The description should be brief, as well as thorough.</span></span> <span data-ttu-id="c1f10-139">En outre, n’oubliez pas que si la description du paramètre devient trop longue, par exemple lorsque les deux paramètres interagissent entre eux, vous pouvez ajouter davantage de contenu dans la section Remarques de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c1f10-139">Also, remember that if the parameter description becomes too long, such as when two parameters interact with each other, you can add more content in the NOTES section of the cmdlet Help topic.</span></span>

  <span data-ttu-id="c1f10-140">La description du paramètre fournit deux types d’informations.</span><span class="sxs-lookup"><span data-stu-id="c1f10-140">The parameter description provides two types of information.</span></span>

- <span data-ttu-id="c1f10-141">Ce que l’applet de commande fait lorsque le paramètre est utilisé.</span><span class="sxs-lookup"><span data-stu-id="c1f10-141">What the cmdlet does when the parameter is used.</span></span>

- <span data-ttu-id="c1f10-142">Quelles une valeur autorisée est pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="c1f10-142">What a legal value is for the parameter.</span></span>

- <span data-ttu-id="c1f10-143">Étant donné que les valeurs de paramètre sont exprimées en tant qu’objets .NET Framework, les utilisateurs ont besoin de plus d’informations sur ces valeurs qu’elles le feraient dans une aide en ligne de commande traditionnelle.</span><span class="sxs-lookup"><span data-stu-id="c1f10-143">Because the parameter values are expressed as .NET Framework objects, users need more information about these values than they would in a traditional command-line Help.</span></span> <span data-ttu-id="c1f10-144">Indiquer à quel type de données, le paramètre est conçu pour accepter l’utilisateur et incluent des exemples.</span><span class="sxs-lookup"><span data-stu-id="c1f10-144">Tell the user what type of data the parameter is designed to accept, and include examples.</span></span>

<span data-ttu-id="c1f10-145">La valeur par défaut du paramètre est la valeur qui est utilisée si le paramètre n’est pas spécifié sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="c1f10-145">The default value of the parameter is the value that is used if the parameter is not specified on the command line.</span></span> <span data-ttu-id="c1f10-146">Notez que la valeur par défaut est facultative et n’est pas nécessaire pour certains paramètres, tels que les paramètres requis.</span><span class="sxs-lookup"><span data-stu-id="c1f10-146">Note that the default value is optional, and is not needed for some parameters, such as required parameters.</span></span> <span data-ttu-id="c1f10-147">Toutefois, vous devez spécifier une valeur par défaut pour la plupart des paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="c1f10-147">However, you should specify a default value for most optional parameters.</span></span>

<span data-ttu-id="c1f10-148">La valeur par défaut aide l’utilisateur à comprendre l’effet de ne pas utiliser le paramètre.</span><span class="sxs-lookup"><span data-stu-id="c1f10-148">The default value helps the user to understand the effect of not using the parameter.</span></span> <span data-ttu-id="c1f10-149">Décrire la valeur par défaut d’une manière très spécifique, tel que le « répertoire actif » ou « Windows PowerShell répertoire d’installation ($pshome) » pour un chemin d’accès facultatif.</span><span class="sxs-lookup"><span data-stu-id="c1f10-149">Describe the default value very specifically, such as the "Current directory" or the "Windows PowerShell installation directory ($pshome)" for an optional path.</span></span> <span data-ttu-id="c1f10-150">Vous pouvez également écrire une phrase qui décrit la valeur par défaut, telles que la phrase suivante est utilisée pour le `PassThru` paramètre : « Si PassThru n’est pas spécifié, l’applet de commande ne transmet pas les objets dans le pipeline. »</span><span class="sxs-lookup"><span data-stu-id="c1f10-150">You can also write a sentence that describes the default, such as the following sentence used for the `PassThru` parameter: "If PassThru is not specified, the cmdlet does not pass objects down the pipeline."</span></span>  <span data-ttu-id="c1f10-151">En outre, étant donné que la valeur est affichée en regard du nom du champ «**valeur par défaut**», vous n’avez pas besoin d’inclure le terme « default value » dans l’entrée.</span><span class="sxs-lookup"><span data-stu-id="c1f10-151">Also, because the value is displayed opposite the field name "**Default value**", you do not need to include the term "default value" in the entry.</span></span>

<span data-ttu-id="c1f10-152">La valeur par défaut du paramètre n’est pas affichée dans toutes les vues de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c1f10-152">The default value of the parameter is not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="c1f10-153">Toutefois, il est affiché dans une table (ainsi que les attributs de paramètre) en suivant la description du paramètre lorsque l’utilisateur demande pour la version complète (Get-Help \<cmdletname >-complet) ou un paramètre (Get-Help \<cmdletname >-paramètre) vue de la rubrique.</span><span class="sxs-lookup"><span data-stu-id="c1f10-153">However, it is displayed in a table (along with the parameter attributes) following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

<span data-ttu-id="c1f10-154">Le code XML suivant montre une paire de `<dev:defaultValue>` balises ajoutées à la `<command:parameter>` nœud.</span><span class="sxs-lookup"><span data-stu-id="c1f10-154">The following XML shows a pair of `<dev:defaultValue>` tags added to the `<command:parameter>` node.</span></span> <span data-ttu-id="c1f10-155">Notez que la valeur par défaut suit immédiatement après la fermeture `</command:parameterValue>` balise (lorsque la valeur du paramètre est spécifiée) ou la fermeture `</maml:description>` balise de la description du paramètre.</span><span class="sxs-lookup"><span data-stu-id="c1f10-155">Notice that the default value follows immediately after the closing `</command:parameterValue>` tag (when the parameter value is specified) or the closing `</maml:description>` tag of the parameter description.</span></span> <span data-ttu-id="c1f10-156">Nom.</span><span class="sxs-lookup"><span data-stu-id="c1f10-156">name.</span></span>

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

<span data-ttu-id="c1f10-157">Ajoutez des valeurs pour les Types énumérés</span><span class="sxs-lookup"><span data-stu-id="c1f10-157">Add Values for Enumerated Types</span></span>

<span data-ttu-id="c1f10-158">Si le paramètre a plusieurs valeurs ou les valeurs d’un type énuméré, vous pouvez utiliser un texte facultatif \<dev:possibleValues > nœud.</span><span class="sxs-lookup"><span data-stu-id="c1f10-158">If the parameter has multiple values or values of an enumerated type, you can use an optional \<dev:possibleValues> node.</span></span> <span data-ttu-id="c1f10-159">Ce nœud vous permet de spécifier un nom et une description pour les valeurs multiples.</span><span class="sxs-lookup"><span data-stu-id="c1f10-159">This node allows you to specify a name and description for multiple values.</span></span>

<span data-ttu-id="c1f10-160">N’oubliez pas que les descriptions des valeurs énumérées n’apparaissent pas dans un de la valeur par défaut aide les vues affichées par le `Get-Help` applet de commande, mais les autres visionneuses aide peuvent afficher ce contenu dans leurs vues.</span><span class="sxs-lookup"><span data-stu-id="c1f10-160">Be aware that the descriptions of the enumerated values do not appear in any of the default Help views displayed by the `Get-Help` cmdlet, but other Help viewers may display this content in their views.</span></span>

<span data-ttu-id="c1f10-161">Le code XML suivant montre un `<dev:possibleValues>` nœud avec deux valeurs spécifiées.</span><span class="sxs-lookup"><span data-stu-id="c1f10-161">The following XML shows a `<dev:possibleValues>` node with two values specified.</span></span>

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