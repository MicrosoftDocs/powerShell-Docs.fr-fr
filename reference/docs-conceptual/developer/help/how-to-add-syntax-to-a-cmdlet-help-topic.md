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
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a><span data-ttu-id="c4b05-103">Guide pratique pour ajouter la syntaxe à une rubrique d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="c4b05-103">How to Add Syntax to a Cmdlet Help Topic</span></span>

<span data-ttu-id="c4b05-104">Avant de commencer à coder le XML pour le diagramme de syntaxe dans le fichier d’aide de l’applet de commande, lisez cette section pour obtenir une image claire du type de données que vous devez fournir, telles que les attributs des paramètres, et de la façon dont ces données sont affichées dans le diagramme de syntaxe..</span><span class="sxs-lookup"><span data-stu-id="c4b05-104">Before you start to code the XML for the syntax diagram in the cmdlet Help file, read this section to get a clear picture of the kind of data you need to provide, such as the parameter attributes, and how that data is displayed in the syntax diagram..</span></span>

## <a name="parameter-attributes"></a><span data-ttu-id="c4b05-105">Attributs de paramètre</span><span class="sxs-lookup"><span data-stu-id="c4b05-105">Parameter Attributes</span></span>

- <span data-ttu-id="c4b05-106">Obligatoire</span><span class="sxs-lookup"><span data-stu-id="c4b05-106">Required</span></span>
  - <span data-ttu-id="c4b05-107">Si la valeur est true, le paramètre doit apparaître dans toutes les commandes qui utilisent le jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="c4b05-107">If true, the parameter must appear in all commands that use the parameter set.</span></span>
  - <span data-ttu-id="c4b05-108">Si la valeur est false, le paramètre est facultatif dans toutes les commandes qui utilisent le jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="c4b05-108">If false, the parameter is optional in all commands that use the parameter set.</span></span>
- <span data-ttu-id="c4b05-109">Position</span><span class="sxs-lookup"><span data-stu-id="c4b05-109">Position</span></span>
  - <span data-ttu-id="c4b05-110">S’il est nommé, le nom du paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="c4b05-110">If named, the parameter name is required.</span></span>
  - <span data-ttu-id="c4b05-111">Si positionnel, le nom du paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="c4b05-111">If positional, the parameter name is optional.</span></span> <span data-ttu-id="c4b05-112">Lorsqu’elle est omise, la valeur du paramètre doit se trouver à la position spécifiée dans la commande.</span><span class="sxs-lookup"><span data-stu-id="c4b05-112">When it is omitted, the parameter value must be in the specified position in the command.</span></span> <span data-ttu-id="c4b05-113">Par exemple, si la valeur est position = "1", la valeur du paramètre doit être la première ou la seule valeur de paramètre sans nom dans la commande.</span><span class="sxs-lookup"><span data-stu-id="c4b05-113">For example, if the value is position="1", the parameter value must be the first or only unnamed parameter value in the command.</span></span>
- <span data-ttu-id="c4b05-114">Entrée de pipeline</span><span class="sxs-lookup"><span data-stu-id="c4b05-114">Pipeline Input</span></span>
  - <span data-ttu-id="c4b05-115">Si la valeur est true (ByValue), vous pouvez diriger l’entrée vers le paramètre.</span><span class="sxs-lookup"><span data-stu-id="c4b05-115">If true (ByValue), you can pipe input to the parameter.</span></span> <span data-ttu-id="c4b05-116">L’entrée est associée (« lié à ») au paramètre même si le nom de la propriété et le type d’objet ne correspondent pas au type attendu.</span><span class="sxs-lookup"><span data-stu-id="c4b05-116">The input is associated with ("bound to") the parameter even if the property name and the object type do not match the expected type.</span></span>
    <span data-ttu-id="c4b05-117">Les composants de liaison de paramètres PowerShell essaient de convertir l’entrée dans le type correct et de faire échouer la commande uniquement lorsque le type ne peut pas être converti.</span><span class="sxs-lookup"><span data-stu-id="c4b05-117">The PowerShell parameter binding components try to convert the input to the correct type and fail the command only when the type cannot be converted.</span></span> <span data-ttu-id="c4b05-118">Un seul paramètre d’un jeu de paramètres peut être associé à la valeur.</span><span class="sxs-lookup"><span data-stu-id="c4b05-118">Only one parameter in a parameter set can be associated by value.</span></span>
  - <span data-ttu-id="c4b05-119">Si la valeur est true (ByPropertyName), vous pouvez diriger l’entrée vers le paramètre.</span><span class="sxs-lookup"><span data-stu-id="c4b05-119">If true (ByPropertyName), you can pipe input to the parameter.</span></span> <span data-ttu-id="c4b05-120">Toutefois, l’entrée est associée au paramètre uniquement lorsque le nom du paramètre correspond au nom d’une propriété de l’objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="c4b05-120">However, the input is associated with the parameter only when the parameter name matches the name of a property of the input object.</span></span> <span data-ttu-id="c4b05-121">Par exemple, si le nom du paramètre est `Path` , les objets transmis à l’applet de commande sont associés à ce paramètre uniquement lorsque l’objet a une propriété nommée Path.</span><span class="sxs-lookup"><span data-stu-id="c4b05-121">For example, if the parameter name is `Path`, objects piped to the cmdlet are associated with that parameter only when the object has a property named path.</span></span>
  - <span data-ttu-id="c4b05-122">Si la valeur est true (ByValue, ByPropertyName), vous pouvez diriger l’entrée vers le paramètre à l’aide d’un nom de propriété ou d’une valeur.</span><span class="sxs-lookup"><span data-stu-id="c4b05-122">If true (ByValue, ByPropertyName), you can pipe input to the parameter either by property name or by value.</span></span> <span data-ttu-id="c4b05-123">Un seul paramètre d’un jeu de paramètres peut être associé à la valeur.</span><span class="sxs-lookup"><span data-stu-id="c4b05-123">Only one parameter in a parameter set can be associated by value.</span></span>
  - <span data-ttu-id="c4b05-124">Si la valeur est false, vous ne pouvez pas diriger d’entrée vers ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="c4b05-124">If false, you cannot pipe input to this parameter.</span></span>
- <span data-ttu-id="c4b05-125">Globbing</span><span class="sxs-lookup"><span data-stu-id="c4b05-125">Globbing</span></span>
  - <span data-ttu-id="c4b05-126">Si la valeur est true, le texte que l’utilisateur tape pour la valeur de paramètre peut inclure des caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="c4b05-126">If true, the text that the user types for the parameter value can include wildcard characters.</span></span>
  - <span data-ttu-id="c4b05-127">Si la valeur est false, le texte que l’utilisateur tape pour la valeur de paramètre ne peut pas inclure de caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="c4b05-127">If false, the text that the user types for the parameter value cannot include wildcard characters.</span></span>

### <a name="parameter-value-attributes"></a><span data-ttu-id="c4b05-128">Attributs de valeur de paramètre</span><span class="sxs-lookup"><span data-stu-id="c4b05-128">Parameter Value Attributes</span></span>

- <span data-ttu-id="c4b05-129">Obligatoire</span><span class="sxs-lookup"><span data-stu-id="c4b05-129">Required</span></span>
  - <span data-ttu-id="c4b05-130">Si la valeur est true, la valeur spécifiée doit être utilisée chaque fois que le paramètre est utilisé dans une commande.</span><span class="sxs-lookup"><span data-stu-id="c4b05-130">If true, the specified value must be used whenever using the parameter in a command.</span></span>
  - <span data-ttu-id="c4b05-131">Si la valeur est false, la valeur du paramètre est facultative.</span><span class="sxs-lookup"><span data-stu-id="c4b05-131">If false, the parameter value is optional.</span></span> <span data-ttu-id="c4b05-132">En règle générale, une valeur est facultative uniquement lorsqu’il s’agit de l’une des nombreuses valeurs valides pour un paramètre, par exemple dans un type énuméré.</span><span class="sxs-lookup"><span data-stu-id="c4b05-132">Typically, a value is optional only when it is one of several valid values for a parameter, such as in an enumerated type.</span></span>

<span data-ttu-id="c4b05-133">L’attribut **requis** d’une valeur de paramètre est différent de l’attribut **requis** d’un paramètre.</span><span class="sxs-lookup"><span data-stu-id="c4b05-133">The **Required** attribute of a parameter value is different from the **Required** attribute of a parameter.</span></span>

<span data-ttu-id="c4b05-134">L’attribut required d’un paramètre indique si le paramètre (et sa valeur) doit être inclus lors de l’appel de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c4b05-134">The required attribute of a parameter indicates whether the parameter (and its value) must be included when invoking the cmdlet.</span></span> <span data-ttu-id="c4b05-135">En revanche, l’attribut required d’une valeur de paramètre est utilisé uniquement lorsque le paramètre est inclus dans la commande.</span><span class="sxs-lookup"><span data-stu-id="c4b05-135">In contrast, the required attribute of a parameter value is used only when the parameter is included in the command.</span></span> <span data-ttu-id="c4b05-136">Elle indique si cette valeur particulière doit être utilisée avec le paramètre.</span><span class="sxs-lookup"><span data-stu-id="c4b05-136">It indicates whether that particular value must be used with the parameter.</span></span>

<span data-ttu-id="c4b05-137">En règle générale, les valeurs de paramètre qui sont des espaces réservés sont obligatoires et les valeurs de paramètre qui sont des littéraux ne sont pas requises, car il s’agit de l’une des nombreuses valeurs qui peuvent être utilisées avec le paramètre.</span><span class="sxs-lookup"><span data-stu-id="c4b05-137">Typically, parameter values that are placeholders are required and parameter values that are literal are not required, because they are one of several values that might be used with the parameter.</span></span>

### <a name="gathering-syntax-information"></a><span data-ttu-id="c4b05-138">Collecte d’informations de syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4b05-138">Gathering Syntax Information</span></span>

1. <span data-ttu-id="c4b05-139">Commencez par le nom de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c4b05-139">Start with the cmdlet name.</span></span>

   ```
   SYNTAX
       Get-Tech
   ```

1. <span data-ttu-id="c4b05-140">Répertorie tous les paramètres de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c4b05-140">List all the parameters of the cmdlet.</span></span> <span data-ttu-id="c4b05-141">Tapez un trait d’Union ( `-` ) (ASCII 45) avant chaque nom de paramètre.</span><span class="sxs-lookup"><span data-stu-id="c4b05-141">Type a hyphen (`-`) (ASCII 45) before each parameter name.</span></span>
   <span data-ttu-id="c4b05-142">Séparez les paramètres en jeux de paramètres (certaines applets de commande ne peuvent avoir qu’un seul jeu de paramètres).</span><span class="sxs-lookup"><span data-stu-id="c4b05-142">Separate the parameters into parameter sets (some cmdlets may have only one parameter set).</span></span> <span data-ttu-id="c4b05-143">Dans cet exemple, l’applet de commande Get-Tech a deux jeux de paramètres.</span><span class="sxs-lookup"><span data-stu-id="c4b05-143">In this example the Get-Tech cmdlet has two parameter sets.</span></span>

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   <span data-ttu-id="c4b05-144">Démarrez chaque jeu de paramètres avec le nom de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c4b05-144">Start each parameter set with the cmdlet name.</span></span>

   <span data-ttu-id="c4b05-145">Répertoriez d’abord le jeu de paramètres par défaut.</span><span class="sxs-lookup"><span data-stu-id="c4b05-145">List the default parameter set first.</span></span> <span data-ttu-id="c4b05-146">Le paramètre par défaut est spécifié par la classe cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c4b05-146">The default parameter is specified by the cmdlet class.</span></span>

   <span data-ttu-id="c4b05-147">Pour chaque jeu de paramètres, listez son paramètre unique en premier, sauf s’il existe des paramètres positionnels qui doivent apparaître en premier.</span><span class="sxs-lookup"><span data-stu-id="c4b05-147">For each parameter set, list its unique parameter first, unless there are positional parameters that must appear first.</span></span> <span data-ttu-id="c4b05-148">Dans l’exemple précédent, les paramètres Name et ID sont des paramètres uniques pour les deux jeux de paramètres (chaque jeu de paramètres doit avoir un paramètre unique pour ce jeu de paramètres).</span><span class="sxs-lookup"><span data-stu-id="c4b05-148">In the previous example, the Name and ID parameters are unique parameters for the two parameter sets (each parameter set must have one parameter that is unique to that parameter set).</span></span> <span data-ttu-id="c4b05-149">Cela permet aux utilisateurs d’identifier plus facilement le paramètre qu’ils doivent fournir pour le jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="c4b05-149">This makes it easier for users to identify what parameter they need to supply for the parameter set.</span></span>

   <span data-ttu-id="c4b05-150">Répertoriez les paramètres dans l’ordre dans lequel ils doivent apparaître dans la commande.</span><span class="sxs-lookup"><span data-stu-id="c4b05-150">List the parameters in the order that they should appear in the command.</span></span> <span data-ttu-id="c4b05-151">Si l’ordre n’a pas d’importance, listez les paramètres associés ou répertoriez d’abord les paramètres les plus fréquemment utilisés.</span><span class="sxs-lookup"><span data-stu-id="c4b05-151">If the order does not matter, list related parameters together, or list the most frequently used parameters first.</span></span>

   <span data-ttu-id="c4b05-152">Veillez à répertorier les paramètres WhatIf et Confirm si l’applet de commande prend en charge ShouldProcess.</span><span class="sxs-lookup"><span data-stu-id="c4b05-152">Be sure to list the WhatIf and Confirm parameters if the cmdlet supports ShouldProcess.</span></span>

   <span data-ttu-id="c4b05-153">Ne répertoriez pas les paramètres communs (tels que verbose, Debug et ErrorAction) dans votre diagramme de syntaxe.</span><span class="sxs-lookup"><span data-stu-id="c4b05-153">Do not list the common parameters (such as Verbose, Debug, and ErrorAction) in your syntax diagram.</span></span> <span data-ttu-id="c4b05-154">L' `Get-Help` applet de commande ajoute ces informations lors de l’affichage de la rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="c4b05-154">The `Get-Help` cmdlet adds that information for you when it displays the Help topic.</span></span>

1. <span data-ttu-id="c4b05-155">Ajoutez les valeurs des paramètres.</span><span class="sxs-lookup"><span data-stu-id="c4b05-155">Add the parameter values.</span></span> <span data-ttu-id="c4b05-156">Dans PowerShell, les valeurs de paramètres sont représentées par leur type .NET.</span><span class="sxs-lookup"><span data-stu-id="c4b05-156">In PowerShell, parameter values are represented by their .NET type.</span></span>
   <span data-ttu-id="c4b05-157">Toutefois, le nom de type peut être abrégé, par exemple « String » pour System. String.</span><span class="sxs-lookup"><span data-stu-id="c4b05-157">However, the type name can be abbreviated, such as "string" for System.String.</span></span>

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   <span data-ttu-id="c4b05-158">Abrégez les types tant que leur signification est claire, telle que **String** pour **System. String** et **int** pour **System. Int32**.</span><span class="sxs-lookup"><span data-stu-id="c4b05-158">Abbreviate types as long as their meaning is clear, such as **string** for **System.String** and **int** for **System.Int32**.</span></span>

   <span data-ttu-id="c4b05-159">Répertorie toutes les valeurs des énumérations, telles que le `-type` paramètre dans l’exemple précédent, qui peut être défini sur de **base** ou **avancé**.</span><span class="sxs-lookup"><span data-stu-id="c4b05-159">List all values of enumerations, such as the `-type` parameter in the previous example, which can be set to **basic** or **advanced**.</span></span>

   <span data-ttu-id="c4b05-160">Les paramètres de commutateur, comme `-list` dans l’exemple précédent, n’ont pas de valeurs.</span><span class="sxs-lookup"><span data-stu-id="c4b05-160">Switch parameters, such as `-list` in the previous example, do not have values.</span></span>

1. <span data-ttu-id="c4b05-161">Ajoutez des crochets pointus aux valeurs de paramètres qui sont des espaces réservés, par rapport aux valeurs de paramètres qui sont des littéraux.</span><span class="sxs-lookup"><span data-stu-id="c4b05-161">Add angle brackets to parameters values that are placeholder, as compared to parameter values that are literals.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

1. <span data-ttu-id="c4b05-162">Placez les paramètres facultatifs et leurs valeurs entre crochets.</span><span class="sxs-lookup"><span data-stu-id="c4b05-162">Enclose optional parameters and their vales in square brackets.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

1. <span data-ttu-id="c4b05-163">Placez les noms de paramètres facultatifs (pour les paramètres positionnels) entre crochets.</span><span class="sxs-lookup"><span data-stu-id="c4b05-163">Enclose optional parameters names (for positional parameters) in square brackets.</span></span> <span data-ttu-id="c4b05-164">Le nom des paramètres qui sont positionnels, tels que le paramètre Name dans l’exemple suivant, n’a pas besoin d’être inclus dans la commande.</span><span class="sxs-lookup"><span data-stu-id="c4b05-164">The name for parameters that are positional, such as the Name parameter in the following example, do not have to be included in the command.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

1. <span data-ttu-id="c4b05-165">Si une valeur de paramètre peut contenir plusieurs valeurs, telles qu’une liste de noms dans le paramètre Name, ajoutez une paire de crochets directement après la valeur du paramètre.</span><span class="sxs-lookup"><span data-stu-id="c4b05-165">If a parameter value can contain multiple values, such as a list of names in the Name parameter, add a pair of square brackets directly following the parameter value.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

1. <span data-ttu-id="c4b05-166">Si l’utilisateur peut choisir parmi des paramètres ou des valeurs de paramètre, tels que le paramètre de type, mettez les choix entre accolades et séparez-les par le symbole OR exclusif (;).</span><span class="sxs-lookup"><span data-stu-id="c4b05-166">If the user can choose from parameters or parameter values, such as the Type parameter, enclose the choices in curly brackets and separate them with the exclusive OR symbol(;).</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

1. <span data-ttu-id="c4b05-167">Si la valeur du paramètre doit utiliser une mise en forme spécifique, telle que des guillemets ou des parenthèses, affichez le format dans la syntaxe.</span><span class="sxs-lookup"><span data-stu-id="c4b05-167">If the parameter value must use specific formatting, such as quotation marks or parentheses, show the format in the syntax.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a><span data-ttu-id="c4b05-168">Codage du diagramme XML de la syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4b05-168">Coding the Syntax Diagram XML</span></span>

<span data-ttu-id="c4b05-169">Le nœud de syntaxe du fichier XML commence immédiatement après le nœud Description, qui se termine par la `</maml:description>` balise.</span><span class="sxs-lookup"><span data-stu-id="c4b05-169">The syntax node of the XML begins immediately after the description node, which ends with the `</maml:description>` tag.</span></span> <span data-ttu-id="c4b05-170">Pour plus d’informations sur la collecte des données utilisées dans le diagramme de syntaxe, consultez [collecte d’informations de syntaxe](#gathering-syntax-information).</span><span class="sxs-lookup"><span data-stu-id="c4b05-170">For information about gathering the data used in the syntax diagram, see [Gathering Syntax Information](#gathering-syntax-information).</span></span>

### <a name="adding-a-syntax-node"></a><span data-ttu-id="c4b05-171">Ajout d’un nœud de syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4b05-171">Adding a Syntax Node</span></span>

<span data-ttu-id="c4b05-172">Le diagramme de syntaxe affiché dans la rubrique d’aide de l’applet de commande est généré à partir des données du nœud de syntaxe du XML.</span><span class="sxs-lookup"><span data-stu-id="c4b05-172">The syntax diagram displayed in the cmdlet Help topic is generated from the data in the syntax node of the XML.</span></span> <span data-ttu-id="c4b05-173">Le nœud de syntaxe est placé entre deux `<command:syntax>` balises.</span><span class="sxs-lookup"><span data-stu-id="c4b05-173">The syntax node is enclosed in a pair if `<command:syntax>` tags.</span></span> <span data-ttu-id="c4b05-174">Avec chaque jeu de paramètres de l’applet de commande placée dans une paire de `<command:syntaxitem>` balises.</span><span class="sxs-lookup"><span data-stu-id="c4b05-174">With each parameter set of the cmdlet enclosed in a pair of `<command:syntaxitem>` tags.</span></span> <span data-ttu-id="c4b05-175">Il n’existe aucune limite au nombre de `<command:syntaxitem>` balises que vous pouvez ajouter.</span><span class="sxs-lookup"><span data-stu-id="c4b05-175">There is no limit to the number of `<command:syntaxitem>` tags that you can add.</span></span>

<span data-ttu-id="c4b05-176">L’exemple suivant montre un nœud de syntaxe qui possède des nœuds élément de syntaxe pour deux jeux de paramètres.</span><span class="sxs-lookup"><span data-stu-id="c4b05-176">The following example shows a syntax node that has syntax item nodes for two parameter sets.</span></span>

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

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a><span data-ttu-id="c4b05-177">Ajout du nom de l’applet de commande aux données du jeu de paramètres</span><span class="sxs-lookup"><span data-stu-id="c4b05-177">Adding the Cmdlet Name to the Parameter Set Data</span></span>

<span data-ttu-id="c4b05-178">Chaque jeu de paramètres de l’applet de commande est spécifié dans un nœud élément de syntaxe.</span><span class="sxs-lookup"><span data-stu-id="c4b05-178">Each parameter set of the cmdlet is specified in a syntax item node.</span></span> <span data-ttu-id="c4b05-179">Chaque nœud d’élément de syntaxe commence par une paire de `<maml:name>` balises qui inclut le nom de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c4b05-179">Each syntax item node begins with a pair of `<maml:name>` tags that include the name of the cmdlet.</span></span>

<span data-ttu-id="c4b05-180">L’exemple suivant inclut un nœud de syntaxe qui possède des nœuds élément de syntaxe pour deux jeux de paramètres.</span><span class="sxs-lookup"><span data-stu-id="c4b05-180">The following example includes a syntax node that has syntax item nodes for two parameter sets.</span></span>

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

### <a name="adding-parameters"></a><span data-ttu-id="c4b05-181">Ajouter des paramètres</span><span class="sxs-lookup"><span data-stu-id="c4b05-181">Adding Parameters</span></span>

<span data-ttu-id="c4b05-182">Chaque paramètre ajouté au nœud élément de syntaxe est spécifié dans une paire de `<command:parameter>` balises.</span><span class="sxs-lookup"><span data-stu-id="c4b05-182">Each parameter added to the syntax item node is specified within a pair of `<command:parameter>` tags.</span></span> <span data-ttu-id="c4b05-183">Vous avez besoin d’une paire de `<command:parameter>` balises pour chaque paramètre inclus dans le jeu de paramètres, à l’exception des paramètres communs fournis par PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c4b05-183">You need a pair of `<command:parameter>` tags for each parameter included in the parameter set, with the exception of the common parameters that are provided by PowerShell.</span></span>

<span data-ttu-id="c4b05-184">Les attributs de la `<command:parameter>` balise d’ouverture déterminent la façon dont le paramètre apparaît dans le diagramme de syntaxe.</span><span class="sxs-lookup"><span data-stu-id="c4b05-184">The attributes of the opening `<command:parameter>` tag determine how the parameter appears in the syntax diagram.</span></span> <span data-ttu-id="c4b05-185">Pour plus d’informations sur les attributs de paramètres, consultez [attributs de paramètres](#parameter-attributes).</span><span class="sxs-lookup"><span data-stu-id="c4b05-185">For information on parameter attributes, see [Parameter Attributes](#parameter-attributes).</span></span>

> [!NOTE]
> <span data-ttu-id="c4b05-186">La `<command:parameter>` balise prend en charge un élément enfant `<maml:description>` dont le contenu n’est jamais affiché.</span><span class="sxs-lookup"><span data-stu-id="c4b05-186">The `<command:parameter>` tag supports a child element `<maml:description>` whose content is never displayed.</span></span> <span data-ttu-id="c4b05-187">Les descriptions des paramètres sont spécifiées dans le nœud du paramètre du XML.</span><span class="sxs-lookup"><span data-stu-id="c4b05-187">The parameter descriptions are specified in the parameter node of the XML.</span></span> <span data-ttu-id="c4b05-188">Pour éviter les incohérences entre les informations de l’élément de syntaxe Bodes et le nœud de paramètre, omettez le ( `<maml:description>` ou laissez-le vide.</span><span class="sxs-lookup"><span data-stu-id="c4b05-188">To avoid inconsistencies between the information in the syntax item bodes and the parameter node, omit the (`<maml:description>` or leave it empty.</span></span>

<span data-ttu-id="c4b05-189">L’exemple suivant comprend un nœud élément de syntaxe pour un jeu de paramètres avec deux paramètres.</span><span class="sxs-lookup"><span data-stu-id="c4b05-189">The following example includes a syntax item node for a parameter set with two parameters.</span></span>

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
