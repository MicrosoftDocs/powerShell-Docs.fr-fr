---
ms.date: 09/12/2016
ms.topic: reference
title: Guide pratique pour ajouter des informations sur les paramètres
description: Guide pratique pour ajouter des informations sur les paramètres
ms.openlocfilehash: 8f4fc46ef256a77b058df4ba506124f80732cb39
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92663046"
---
# <a name="how-to-add-parameter-information"></a><span data-ttu-id="f3d0c-103">Guide pratique pour ajouter des informations sur les paramètres</span><span class="sxs-lookup"><span data-stu-id="f3d0c-103">How to Add Parameter Information</span></span>

<span data-ttu-id="f3d0c-104">Cette section décrit comment ajouter du contenu qui s’affiche dans la section **paramètres** de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-104">This section describes how to add content that is displayed in the **PARAMETERS** section of the cmdlet Help topic.</span></span> <span data-ttu-id="f3d0c-105">La section **paramètres** de la rubrique d’aide répertorie chacun des paramètres de l’applet de commande et fournit une description détaillée de chaque paramètre.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-105">The **PARAMETERS** section of the Help topic lists each of the parameters of the cmdlet and provides a detailed description of each parameter.</span></span>

<span data-ttu-id="f3d0c-106">Le contenu de la section des **paramètres** doit être cohérent avec le contenu de la section **syntaxe** de la rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-106">The content of the **PARAMETERS** section should be consistent with the content of the **SYNTAX** section of the Help topic.</span></span> <span data-ttu-id="f3d0c-107">Il incombe à l’auteur de l’aide de s’assurer que le nœud de **syntaxe** et de **paramètres** contient des éléments XML similaires.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-107">It is the responsibility of the Help author to make sure that both the **Syntax** and **Parameters** node contain similar XML elements.</span></span>

> [!NOTE]
> <span data-ttu-id="f3d0c-108">Pour obtenir une vue complète d’un fichier d’aide, ouvrez l’un des `dll-Help.xml` fichiers situés dans le répertoire d’installation de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-108">For a complete view of a Help file, open one of the `dll-Help.xml` files located in the PowerShell installation directory.</span></span> <span data-ttu-id="f3d0c-109">Par exemple, le `Microsoft.PowerShell.Commands.Management.dll-Help.xml` fichier contient du contenu pour plusieurs des applets de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-109">For example, the `Microsoft.PowerShell.Commands.Management.dll-Help.xml` file contains content for several of the PowerShell cmdlets.</span></span>

### <a name="to-add-parameters"></a><span data-ttu-id="f3d0c-110">Pour ajouter des paramètres</span><span class="sxs-lookup"><span data-stu-id="f3d0c-110">To Add Parameters</span></span>

1. <span data-ttu-id="f3d0c-111">Ouvrez le fichier d’aide de l’applet de commande et recherchez le nœud de commande pour l’applet de commande que vous documentez.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-111">Open the cmdlet Help file and locate the Command node for the cmdlet you are documenting.</span></span> <span data-ttu-id="f3d0c-112">Si vous ajoutez une nouvelle applet de commande, vous devez créer un nouveau nœud de commande.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-112">If you are adding a new cmdlet you will need to create a new Command node.</span></span> <span data-ttu-id="f3d0c-113">Votre fichier d’aide contiendra un nœud de commande pour chaque cmdlet pour laquelle vous fournissez du contenu d’aide.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-113">Your Help file will contain a Command node for each cmdlet that you are providing Help content for.</span></span> <span data-ttu-id="f3d0c-114">Voici un exemple de nœud de commande vide.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-114">Here is an example of a blank Command node.</span></span>

    ```xml
    <command:command>
    </command:command>
    ```

1. <span data-ttu-id="f3d0c-115">Dans le nœud de commande, localisez le nœud Description et ajoutez un nœud paramètres comme indiqué ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-115">Within the Command node, locate the Description node and add a Parameters node as shown below.</span></span>
   <span data-ttu-id="f3d0c-116">Un seul nœud de paramètres est autorisé et il doit suivre immédiatement le nœud de syntaxe.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-116">Only one Parameters node is allowed, and it should immediately follow the Syntax node.</span></span>

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

1. <span data-ttu-id="f3d0c-117">Dans le nœud Paramètres, ajoutez un nœud de **paramètre** pour chaque paramètre de l’applet de commande, comme indiqué ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-117">Within the Parameters node, add a **Parameter** node for each parameter of the cmdlet as shown below.</span></span>

   <span data-ttu-id="f3d0c-118">Dans cet exemple, un nœud de **paramètre** est ajouté pour trois paramètres.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-118">In this example, a **Parameter** node is added for three parameters.</span></span>

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   <span data-ttu-id="f3d0c-119">Étant donné que ces balises XML sont les mêmes que celles utilisées dans le nœud de syntaxe et que les paramètres spécifiés ici doivent correspondre aux paramètres spécifiés par le nœud de syntaxe, vous pouvez copier les nœuds de paramètres à partir du nœud de syntaxe et les coller dans le nœud Paramètres.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-119">Because these are the same XML tags that are used in the Syntax node, and because the parameters specified here must match the parameters specified by the Syntax node, you can copy the Parameter nodes from the Syntax node and paste them into the Parameters node.</span></span> <span data-ttu-id="f3d0c-120">Toutefois, veillez à ne copier qu’une seule instance d’un nœud de paramètre, même si le paramètre est spécifié dans plusieurs jeux de paramètres dans la syntaxe.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-120">However, be sure to copy only one instance of a Parameter node, even if the parameter is specified in multiple parameter sets in the syntax.</span></span>

1. <span data-ttu-id="f3d0c-121">Pour chaque nœud de paramètre, définissez les valeurs d’attribut qui définissent les caractéristiques de chaque paramètre.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-121">For each Parameter node, set the attribute values that define the characteristics of each parameter.</span></span> <span data-ttu-id="f3d0c-122">Ces attributs sont les suivants : required, globbing, PipelineInput et position.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-122">These attributes include the following: required, globbing, pipelineinput, and position.</span></span>

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

1. <span data-ttu-id="f3d0c-123">Pour chaque nœud de paramètre, ajoutez le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-123">For each Parameter node, add the name of the parameter.</span></span> <span data-ttu-id="f3d0c-124">Voici un exemple de nom de paramètre ajouté au nœud de paramètre.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-124">Here is an example of the parameter name added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

1. <span data-ttu-id="f3d0c-125">Pour chaque nœud de **paramètre** , ajoutez la description du paramètre.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-125">For each **Parameter** node, add the description of the parameter.</span></span> <span data-ttu-id="f3d0c-126">Voici un exemple de la description de paramètre ajoutée au nœud de **paramètre** .</span><span class="sxs-lookup"><span data-stu-id="f3d0c-126">Here is an example of the parameter description added to the **Parameter** node.</span></span>

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

1. <span data-ttu-id="f3d0c-127">Pour chaque nœud de **paramètre** , ajoutez le type .net du paramètre.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-127">For each **Parameter** node, add the .NET type of the parameter.</span></span> <span data-ttu-id="f3d0c-128">Le type de paramètre est affiché avec le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-128">The parameter type is displayed along with the parameter name.</span></span>

   <span data-ttu-id="f3d0c-129">Voici un exemple de type .NET de paramètre ajouté au nœud de **paramètre** .</span><span class="sxs-lookup"><span data-stu-id="f3d0c-129">Here is an example of the parameter .NET type added to the **Parameter** node.</span></span>

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

1. <span data-ttu-id="f3d0c-130">Pour chaque nœud de **paramètre** , ajoutez la valeur par défaut du paramètre.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-130">For each **Parameter** node, add the default value of the parameter.</span></span> <span data-ttu-id="f3d0c-131">La phrase suivante est ajoutée à la description du paramètre lorsque le contenu est affiché : **DefaultValue** est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-131">The following sentence is added to the parameter description when the content is displayed: **DefaultValue** is the default.</span></span>

   <span data-ttu-id="f3d0c-132">Voici un exemple de la valeur par défaut du paramètre est ajouté au nœud du **paramètre** .</span><span class="sxs-lookup"><span data-stu-id="f3d0c-132">Here is an example of the parameter default value is added to the **Parameter** node.</span></span>

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

1. <span data-ttu-id="f3d0c-133">Pour chaque paramètre ayant plusieurs valeurs, ajoutez un nœud valeurs possibles.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-133">For each Parameter that has multiple values, add a possible values node.</span></span>

   <span data-ttu-id="f3d0c-134">Voici un exemple de l’un des nœuds de valeurs possibles qui définit deux valeurs possibles pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-134">Here is an example of the of a possible values node that defines two possible values for the parameter</span></span>

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

<span data-ttu-id="f3d0c-135">Voici quelques points à retenir lors de l’ajout de paramètres.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-135">Here are some things to remember when adding parameters.</span></span>

- <span data-ttu-id="f3d0c-136">Les attributs du paramètre ne sont pas affichés dans toutes les vues de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-136">The attributes of the parameter are not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="f3d0c-137">Toutefois, ils sont affichés dans un tableau qui suit la description du paramètre lorsque l’utilisateur demande la vue **complète** ( `Get-Help <cmdletname> -full` ) ou du **paramètre** ( `Get-Help <cmdletname> -parameter` ) de la rubrique.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-137">However, they are displayed in a table following the parameter description when the user asks for the **Full** (`Get-Help <cmdletname> -full`) or **Parameter** (`Get-Help <cmdletname> -parameter`) view of the topic.</span></span>

- <span data-ttu-id="f3d0c-138">La description du paramètre est l’une des parties les plus importantes d’une rubrique d’aide sur une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-138">The parameter description is one of the most important parts of a cmdlet Help topic.</span></span> <span data-ttu-id="f3d0c-139">La description doit être brève, ainsi que minutieusement.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-139">The description should be brief, as well as thorough.</span></span> <span data-ttu-id="f3d0c-140">En outre, n’oubliez pas que si la description du paramètre devient trop longue, par exemple quand deux paramètres interagissent entre eux, vous pouvez ajouter du contenu dans la section Remarques de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-140">Also, remember that if the parameter description becomes too long, such as when two parameters interact with each other, you can add more content in the NOTES section of the cmdlet Help topic.</span></span>

  <span data-ttu-id="f3d0c-141">La description du paramètre fournit deux types d’informations.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-141">The parameter description provides two types of information.</span></span>

- <span data-ttu-id="f3d0c-142">Ce que fait l’applet de commande lorsque le paramètre est utilisé.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-142">What the cmdlet does when the parameter is used.</span></span>

- <span data-ttu-id="f3d0c-143">Ce qu’est une valeur légale pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-143">What a legal value is for the parameter.</span></span>

- <span data-ttu-id="f3d0c-144">Étant donné que les valeurs des paramètres sont exprimées en tant qu’objets .NET, les utilisateurs ont besoin de plus d’informations sur ces valeurs que dans une aide de ligne de commande classique.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-144">Because the parameter values are expressed as .NET objects, users need more information about these values than they would in a traditional command-line Help.</span></span> <span data-ttu-id="f3d0c-145">Indiquez à l’utilisateur le type de données que le paramètre est destiné à accepter et incluez des exemples.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-145">Tell the user what type of data the parameter is designed to accept, and include examples.</span></span>

<span data-ttu-id="f3d0c-146">La valeur par défaut du paramètre est la valeur utilisée si le paramètre n’est pas spécifié sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-146">The default value of the parameter is the value that is used if the parameter is not specified on the command line.</span></span> <span data-ttu-id="f3d0c-147">Notez que la valeur par défaut est facultative et n’est pas nécessaire pour certains paramètres, tels que les paramètres requis.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-147">Note that the default value is optional, and is not needed for some parameters, such as required parameters.</span></span> <span data-ttu-id="f3d0c-148">Toutefois, vous devez spécifier une valeur par défaut pour la plupart des paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-148">However, you should specify a default value for most optional parameters.</span></span>

<span data-ttu-id="f3d0c-149">La valeur par défaut permet à l’utilisateur de comprendre l’effet de ne pas utiliser le paramètre.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-149">The default value helps the user to understand the effect of not using the parameter.</span></span> <span data-ttu-id="f3d0c-150">Décrivez la valeur par défaut de manière très spécifique, par exemple le « répertoire actif » ou le « répertoire d’installation PowerShell ( `$PSHOME` ) » pour un chemin d’accès facultatif.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-150">Describe the default value very specifically, such as the "Current directory" or the "PowerShell installation directory (`$PSHOME`)" for an optional path.</span></span> <span data-ttu-id="f3d0c-151">Vous pouvez également écrire une phrase qui décrit la valeur par défaut, telle que la phrase suivante utilisée pour le paramètre **PassThru** : « si PassThru n’est pas spécifié, l’applet de commande ne passe pas d’objets dans le pipeline ».</span><span class="sxs-lookup"><span data-stu-id="f3d0c-151">You can also write a sentence that describes the default, such as the following sentence used for the **PassThru** parameter: "If PassThru is not specified, the cmdlet does not pass objects down the pipeline."</span></span> <span data-ttu-id="f3d0c-152">En outre, étant donné que la valeur est affichée en regard de la **valeur par défaut** du nom de champ, vous n’avez pas besoin d’inclure le terme « valeur par défaut » dans l’entrée.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-152">Also, because the value is displayed opposite the field name **Default value**, you do not need to include the term "default value" in the entry.</span></span>

<span data-ttu-id="f3d0c-153">La valeur par défaut du paramètre n’est pas affichée dans toutes les vues de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-153">The default value of the parameter is not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="f3d0c-154">Toutefois, il est affiché dans une table (avec les attributs de paramètre) qui suit la description du paramètre lorsque l’utilisateur demande la vue **complète** ( `Get-Help <cmdletname> -full` ) ou de **paramètre** ( `Get-Help
<cmdletname> -parameter` ) de la rubrique.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-154">However, it is displayed in a table (along with the parameter attributes) following the parameter description when the user asks for the **Full** (`Get-Help <cmdletname> -full`) or **Parameter** (`Get-Help
<cmdletname> -parameter`) view of the topic.</span></span>

<span data-ttu-id="f3d0c-155">Le code XML suivant montre une paire de `<dev:defaultValue>` balises ajoutées au `<command:parameter>` nœud.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-155">The following XML shows a pair of `<dev:defaultValue>` tags added to the `<command:parameter>` node.</span></span>
<span data-ttu-id="f3d0c-156">Notez que la valeur par défaut suit immédiatement après la `</command:parameterValue>` balise de fermeture (lorsque la valeur du paramètre est spécifiée) ou la `</maml:description>` balise de fermeture de la description du paramètre.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-156">Notice that the default value follows immediately after the closing `</command:parameterValue>` tag (when the parameter value is specified) or the closing `</maml:description>` tag of the parameter description.</span></span> <span data-ttu-id="f3d0c-157">nom.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-157">name.</span></span>

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

<span data-ttu-id="f3d0c-158">Ajouter des valeurs pour les types énumérés</span><span class="sxs-lookup"><span data-stu-id="f3d0c-158">Add Values for Enumerated Types</span></span>

<span data-ttu-id="f3d0c-159">Si le paramètre a plusieurs valeurs ou valeurs d’un type énuméré, vous pouvez utiliser un nœud facultatif \<dev:possibleValues> .</span><span class="sxs-lookup"><span data-stu-id="f3d0c-159">If the parameter has multiple values or values of an enumerated type, you can use an optional \<dev:possibleValues> node.</span></span> <span data-ttu-id="f3d0c-160">Ce nœud vous permet de spécifier un nom et une description pour plusieurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-160">This node allows you to specify a name and description for multiple values.</span></span>

<span data-ttu-id="f3d0c-161">Sachez que les descriptions des valeurs énumérées n’apparaissent pas dans les vues d’aide par défaut affichées par l’applet de commande `Get-Help` , mais d’autres observateurs d’aide peuvent afficher ce contenu dans leurs vues.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-161">Be aware that the descriptions of the enumerated values do not appear in any of the default Help views displayed by the `Get-Help` cmdlet, but other Help viewers may display this content in their views.</span></span>

<span data-ttu-id="f3d0c-162">Le code XML suivant montre un `<dev:possibleValues>` nœud avec deux valeurs spécifiées.</span><span class="sxs-lookup"><span data-stu-id="f3d0c-162">The following XML shows a `<dev:possibleValues>` node with two values specified.</span></span>

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
