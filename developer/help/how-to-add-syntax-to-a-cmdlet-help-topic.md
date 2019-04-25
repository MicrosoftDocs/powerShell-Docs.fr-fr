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
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a><span data-ttu-id="3ef59-102">Guide pratique pour ajouter la syntaxe à une rubrique d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="3ef59-102">How to Add Syntax to a Cmdlet Help Topic</span></span>

- [<span data-ttu-id="3ef59-103">Attributs de paramètre</span><span class="sxs-lookup"><span data-stu-id="3ef59-103">Parameter Attributes</span></span>](#Parameter-Attributes)

- [<span data-ttu-id="3ef59-104">Attributs de valeur de paramètre</span><span class="sxs-lookup"><span data-stu-id="3ef59-104">Parameter Value Attributes</span></span>](#Parameter-Value-Attributes)

- [<span data-ttu-id="3ef59-105">Collecte des informations sur la syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ef59-105">Gathering Syntax Information</span></span>](#Gathering-Syntax-Information)

- [<span data-ttu-id="3ef59-106">Le diagramme de syntaxe XML de codage</span><span class="sxs-lookup"><span data-stu-id="3ef59-106">Coding the Syntax Diagram XML</span></span>](#Coding-the-Syntax-Diagram-XML)

## <a name="things-to-know-about-the-syntax-diagram-in-cmdlet-help"></a><span data-ttu-id="3ef59-107">Choses à savoir sur le diagramme de syntaxe dans l’aide de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="3ef59-107">Things to Know About the Syntax Diagram in Cmdlet Help</span></span>

<span data-ttu-id="3ef59-108">Avant de commencer à coder le code XML pour le diagramme de syntaxe dans le fichier d’aide applet de commande, lisez cette section pour obtenir une vision claire du type de données, que vous devez fournir, telles que les attributs de paramètre et le mode d’affichage de ces données dans le diagramme de syntaxe...</span><span class="sxs-lookup"><span data-stu-id="3ef59-108">Before you start to code the XML for the syntax diagram in the cmdlet Help file, read this section to get a clear picture of the kind of data you need to provide, such as the parameter attributes, and how that data is displayed in the syntax diagram..</span></span>

### <a name="parameter-attributes"></a><span data-ttu-id="3ef59-109">Attributs de paramètre</span><span class="sxs-lookup"><span data-stu-id="3ef59-109">Parameter Attributes</span></span>

- <span data-ttu-id="3ef59-110">Obligatoire</span><span class="sxs-lookup"><span data-stu-id="3ef59-110">Required</span></span>

  - <span data-ttu-id="3ef59-111">Si la valeur est true, le paramètre doit apparaître dans toutes les commandes qui utilisent le jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="3ef59-111">If true, the parameter must appear in all commands that use the parameter set.</span></span>

  - <span data-ttu-id="3ef59-112">Si la valeur est false, le paramètre est facultatif dans toutes les commandes qui utilisent le jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="3ef59-112">If false, the parameter is optional in all commands that use the parameter set.</span></span>

- <span data-ttu-id="3ef59-113">Position</span><span class="sxs-lookup"><span data-stu-id="3ef59-113">Position</span></span>

  - <span data-ttu-id="3ef59-114">Si nommée, le nom de paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="3ef59-114">If named, the parameter name is required.</span></span>

  - <span data-ttu-id="3ef59-115">Si la position, le nom de paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="3ef59-115">If positional, the parameter name is optional.</span></span> <span data-ttu-id="3ef59-116">Lorsqu’il est omis, la valeur du paramètre doit être dans la position spécifiée dans la commande.</span><span class="sxs-lookup"><span data-stu-id="3ef59-116">When it is omitted, the parameter value must be in the specified position in the command.</span></span> <span data-ttu-id="3ef59-117">Par exemple, si la valeur est la position = « 1 », la valeur du paramètre doit être la première ou la seule valeur de paramètre dans la commande sans nom.</span><span class="sxs-lookup"><span data-stu-id="3ef59-117">For example, if the value is position="1", the parameter value must be the first or only unnamed parameter value in the command.</span></span>

- <span data-ttu-id="3ef59-118">Entrée de pipeline</span><span class="sxs-lookup"><span data-stu-id="3ef59-118">Pipeline Input</span></span>

  - <span data-ttu-id="3ef59-119">Si la valeur est true (ByValue), vous pouvez rediriger l’entrée pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="3ef59-119">If true (ByValue), you can pipe input to the parameter.</span></span> <span data-ttu-id="3ef59-120">L’entrée est associée avec (« limite à ») le paramètre même si le nom de propriété et le type d’objet ne correspondent pas au type attendu.</span><span class="sxs-lookup"><span data-stu-id="3ef59-120">The input is associated with ("bound to") the parameter even if the property name and the object type do not match the expected type.</span></span> <span data-ttu-id="3ef59-121">La commande Windows PowerShell ? composants de liaison de paramètre essayez de convertir l’entrée en type correct et de faire échouer la commande uniquement lorsque le type ne peut pas être converti.</span><span class="sxs-lookup"><span data-stu-id="3ef59-121">The Windows PowerShell? parameter binding components try to convert the input to the correct type and fail the command only when the type cannot be converted.</span></span> <span data-ttu-id="3ef59-122">Qu’un seul paramètre dans un jeu de paramètres peut être associé par valeur.</span><span class="sxs-lookup"><span data-stu-id="3ef59-122">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="3ef59-123">Si la valeur est true (ByPropertyName), vous pouvez rediriger l’entrée pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="3ef59-123">If true (ByPropertyName), you can pipe input to the parameter.</span></span> <span data-ttu-id="3ef59-124">Toutefois, l’entrée est associée au paramètre uniquement lorsque le nom du paramètre correspond au nom d’une propriété de l’objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="3ef59-124">However, the input is associated with the parameter only when the parameter name matches the name of a property of the input object.</span></span> <span data-ttu-id="3ef59-125">Par exemple, si le nom du paramètre est `Path`, objets dirigés vers l’applet de commande sont associés à ce paramètre uniquement lorsque l’objet a une propriété nommée du chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="3ef59-125">For example, if the parameter name is `Path`, objects piped to the cmdlet are associated with that parameter only when the object has a property named path.</span></span>

  - <span data-ttu-id="3ef59-126">Si la valeur true (ByValue, ByPropertyName), vous pouvez rediriger l’entrée pour le paramètre par nom ou par valeur.</span><span class="sxs-lookup"><span data-stu-id="3ef59-126">If true (ByValue, ByPropertyName), you can pipe input to the parameter either by property name or by value.</span></span> <span data-ttu-id="3ef59-127">Qu’un seul paramètre dans un jeu de paramètres peut être associé par valeur.</span><span class="sxs-lookup"><span data-stu-id="3ef59-127">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="3ef59-128">Si la valeur est false, vous ne pouvez pas diriger d’entrée pour ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="3ef59-128">If false, you cannot pipe input to this parameter.</span></span>

- <span data-ttu-id="3ef59-129">Utilisation des caractères génériques</span><span class="sxs-lookup"><span data-stu-id="3ef59-129">Globbing</span></span>

  - <span data-ttu-id="3ef59-130">Si la valeur est true, le texte que l’utilisateur tape pour la valeur du paramètre peut inclure des caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="3ef59-130">If true, the text that the user types for the parameter value can include wildcard characters.</span></span>

  - <span data-ttu-id="3ef59-131">Si la valeur est false, le texte que l’utilisateur tape pour la valeur du paramètre ne peut pas inclure des caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="3ef59-131">If false, the text that the user types for the parameter value cannot include wildcard characters.</span></span>

### <a name="parameter-value-attributes"></a><span data-ttu-id="3ef59-132">Attributs de valeur de paramètre</span><span class="sxs-lookup"><span data-stu-id="3ef59-132">Parameter Value Attributes</span></span>

- <span data-ttu-id="3ef59-133">Obligatoire</span><span class="sxs-lookup"><span data-stu-id="3ef59-133">Required</span></span>

  - <span data-ttu-id="3ef59-134">Si la valeur est true, la valeur spécifiée doit être utilisée chaque fois que l’utilisation du paramètre dans une commande.</span><span class="sxs-lookup"><span data-stu-id="3ef59-134">If true, the specified value must be used whenever using the parameter in a command.</span></span>

  - <span data-ttu-id="3ef59-135">Si la valeur est false, la valeur du paramètre est facultative.</span><span class="sxs-lookup"><span data-stu-id="3ef59-135">If false, the parameter value is optional.</span></span> <span data-ttu-id="3ef59-136">En règle générale, une valeur est facultative uniquement lorsqu’il est une de plusieurs valeurs valides pour un paramètre, comme dans un type énuméré.</span><span class="sxs-lookup"><span data-stu-id="3ef59-136">Typically, a value is optional only when it is one of several valid values for a parameter, such as in an enumerated type.</span></span>

<span data-ttu-id="3ef59-137">L’attribut requis d’une valeur de paramètre est différent de l’attribut d’un paramètre requis.</span><span class="sxs-lookup"><span data-stu-id="3ef59-137">The Required attribute of a parameter value is different from the Required attribute of a parameter.</span></span>

<span data-ttu-id="3ef59-138">L’attribut requis d’un paramètre indique si le paramètre (et sa valeur) doivent être incluses lors de l’appel de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3ef59-138">The required attribute of a parameter indicates whether the parameter (and its value) must be included when invoking the cmdlet.</span></span> <span data-ttu-id="3ef59-139">En revanche, l’attribut requis d’une valeur de paramètre est utilisé uniquement lorsque le paramètre est inclus dans la commande.</span><span class="sxs-lookup"><span data-stu-id="3ef59-139">In contrast, the required attribute of a parameter value is used only when the parameter is included in the command.</span></span> <span data-ttu-id="3ef59-140">Cette propriété indique si cette valeur doit être utilisée avec le paramètre.</span><span class="sxs-lookup"><span data-stu-id="3ef59-140">It indicates whether that particular value must be used with the parameter.</span></span>

<span data-ttu-id="3ef59-141">En règle générale, les valeurs de paramètre qui sont des espaces réservés sont requis et les valeurs de paramètre sont littéral ne sont pas requis, car elles sont une des valeurs suivantes qui peuvent être utilisées avec le paramètre.</span><span class="sxs-lookup"><span data-stu-id="3ef59-141">Typically, parameter values that are placeholders are required and parameter values that are literal are not required, because they are one of several values that might be used with the parameter.</span></span>

### <a name="gathering-syntax-information"></a><span data-ttu-id="3ef59-142">Collecte des informations sur la syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ef59-142">Gathering Syntax Information</span></span>

1. <span data-ttu-id="3ef59-143">Démarrer avec le nom de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3ef59-143">Start with the cmdlet name.</span></span>

   ```
   SYNTAX
       Get-Tech
   ```

2. <span data-ttu-id="3ef59-144">Liste de tous les paramètres de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3ef59-144">List all the parameters of the cmdlet.</span></span> <span data-ttu-id="3ef59-145">Tapez un tiret (également appelée « dash » ou « signe » (ASCII 45) devant chaque nom de paramètre.</span><span class="sxs-lookup"><span data-stu-id="3ef59-145">Type a dash (also known as a "dash" or "minus sign" (ASCII 45) before each parameter name.</span></span> <span data-ttu-id="3ef59-146">Séparez les paramètres dans les jeux de paramètres (certaines applets de commande peut avoir qu’un seul paramètre défini).</span><span class="sxs-lookup"><span data-stu-id="3ef59-146">Separate the parameters into parameter sets (some cmdlets may have only one parameter set).</span></span> <span data-ttu-id="3ef59-147">Dans cet exemple le Get-Tech applet de commande a deux jeux de paramètres.</span><span class="sxs-lookup"><span data-stu-id="3ef59-147">In this example the Get-Tech cmdlet has two parameter sets.</span></span>

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   <span data-ttu-id="3ef59-148">Chaque paramètre défini avec le nom de l’applet de commande de démarrage.</span><span class="sxs-lookup"><span data-stu-id="3ef59-148">Start each parameter set with the cmdlet name.</span></span>

   <span data-ttu-id="3ef59-149">Le paramètre par défaut défini au préalable de la liste.</span><span class="sxs-lookup"><span data-stu-id="3ef59-149">List the default parameter set first.</span></span> <span data-ttu-id="3ef59-150">Le paramètre par défaut est spécifié par la classe de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3ef59-150">The default parameter is specified by the cmdlet class.</span></span>

   <span data-ttu-id="3ef59-151">Pour chaque jeu de paramètres, indiquez son paramètre unique tout d’abord, sauf s’il existe des paramètres positionnels qui doivent apparaître en premier.</span><span class="sxs-lookup"><span data-stu-id="3ef59-151">For each parameter set, list its unique parameter first, unless there are positional parameters that must appear first.</span></span> <span data-ttu-id="3ef59-152">Dans l’exemple précédent, les paramètres de nom et l’ID sont des paramètres uniques pour les deux jeux de paramètres (chaque jeu de paramètres doit avoir un seul paramètre qui est unique pour ce jeu de paramètres).</span><span class="sxs-lookup"><span data-stu-id="3ef59-152">In the previous example, the Name and ID parameters are unique parameters for the two parameter sets (each parameter set must have one parameter that is unique to that parameter set).</span></span> <span data-ttu-id="3ef59-153">Cela rend plus facile pour les utilisateurs à identifier quel paramètre dont ils ont besoin pour fournir pour le paramètre défini.</span><span class="sxs-lookup"><span data-stu-id="3ef59-153">This makes it easier for users to identify what parameter they need to supply for the parameter set.</span></span>

   <span data-ttu-id="3ef59-154">Répertorier les paramètres dans l’ordre où ils doivent apparaître dans la commande.</span><span class="sxs-lookup"><span data-stu-id="3ef59-154">List the parameters in the order that they should appear in the command.</span></span> <span data-ttu-id="3ef59-155">Si l’ordre n’a pas d’importance, regrouper les paramètres associés, ou indiquez tout d’abord les paramètres fréquemment utilisés.</span><span class="sxs-lookup"><span data-stu-id="3ef59-155">If the order does not matter, list related parameters together, or list the most frequently used parameters first.</span></span>

   <span data-ttu-id="3ef59-156">Veillez à répertorier les paramètres WhatIf et Confirm si l’applet de commande prend en charge ShouldProcess.</span><span class="sxs-lookup"><span data-stu-id="3ef59-156">Be sure to list the WhatIf and Confirm parameters if the cmdlet supports ShouldProcess.</span></span>

   <span data-ttu-id="3ef59-157">Ne répertorient pas les paramètres communs (tels que Verbose, Debug et ErrorAction) dans votre diagramme de syntaxe.</span><span class="sxs-lookup"><span data-stu-id="3ef59-157">Do not list the common parameters (such as Verbose, Debug, and ErrorAction) in your syntax diagram.</span></span> <span data-ttu-id="3ef59-158">Le `Get-Help` applet de commande ajoute ces informations pour vous lors de l’affichage de la rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="3ef59-158">The `Get-Help` cmdlet adds that information for you when it displays the Help topic.</span></span>

3. <span data-ttu-id="3ef59-159">Ajoutez les valeurs de paramètre.</span><span class="sxs-lookup"><span data-stu-id="3ef59-159">Add the parameter values.</span></span> <span data-ttu-id="3ef59-160">Dans Windows PowerShell ?, les valeurs de paramètre sont représentées par leur type .NET.</span><span class="sxs-lookup"><span data-stu-id="3ef59-160">In Windows PowerShell?, parameter values are represented by their .NET type.</span></span> <span data-ttu-id="3ef59-161">Toutefois, le nom de type peut être abrégé, tel que « string » pour System.String.</span><span class="sxs-lookup"><span data-stu-id="3ef59-161">However, the type name can be abbreviated, such as "string" for System.String.</span></span>

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   <span data-ttu-id="3ef59-162">Abréger types tant que leur signification est claire, tels que « string » pour System.String et « int » pour System.Int32.</span><span class="sxs-lookup"><span data-stu-id="3ef59-162">Abbreviate types as long as their meaning is clear, such as "string" for System.String and "int" for System.Int32.</span></span>

   <span data-ttu-id="3ef59-163">Liste de toutes les valeurs des énumérations, telles que le paramètre - type dans l’exemple précédent, ce qui peut être défini sur « basic » ou « advanced ».</span><span class="sxs-lookup"><span data-stu-id="3ef59-163">List all values of enumerations, such as the -type parameter in the previous example, which can be set to "basic" or "advanced".</span></span>

   <span data-ttu-id="3ef59-164">Passer des paramètres, tels que - liste dans l’exemple précédent, n’ont pas de valeurs.</span><span class="sxs-lookup"><span data-stu-id="3ef59-164">Switch parameters, such as -list in the previous example, do not have values.</span></span>

4. <span data-ttu-id="3ef59-165">Ajouter les crochets pointus aux valeurs de paramètres qui sont l’espace réservé, par rapport aux valeurs de paramètre qui sont des littéraux.</span><span class="sxs-lookup"><span data-stu-id="3ef59-165">Add angle brackets to parameters values that are placeholder, as compared to parameter values that are literals.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. <span data-ttu-id="3ef59-166">Entrez les paramètres facultatifs et leurs valeurs de crochets.</span><span class="sxs-lookup"><span data-stu-id="3ef59-166">Enclose optional parameters and their vales in square brackets.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. <span data-ttu-id="3ef59-167">Placez les noms de paramètres facultatifs (pour les paramètres positionnels) entre crochets.</span><span class="sxs-lookup"><span data-stu-id="3ef59-167">Enclose optional parameters names (for positional parameters) in square brackets.</span></span> <span data-ttu-id="3ef59-168">Le nom pour les paramètres positionnels, tels que le paramètre de nom dans l’exemple suivant, n’ont pas à être inclus dans la commande.</span><span class="sxs-lookup"><span data-stu-id="3ef59-168">The name for parameters that are positional, such as the Name parameter in the following example, do not have to be included in the command.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. <span data-ttu-id="3ef59-169">Si une valeur de paramètre peut contenir plusieurs valeurs, telles qu’une liste de noms dans le paramètre Name, ajoutez une paire de crochets directement après la valeur du paramètre.</span><span class="sxs-lookup"><span data-stu-id="3ef59-169">If a parameter value can contain multiple values, such as a list of names in the Name parameter, add a pair of square brackets directly following the parameter value.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. <span data-ttu-id="3ef59-170">Si l’utilisateur peut choisir à partir des paramètres ou des valeurs de paramètre, tels que le paramètre de Type, placez les choix entre accolades, en les séparant avec le symbol(;) OR exclusif.</span><span class="sxs-lookup"><span data-stu-id="3ef59-170">If the user can choose from parameters or parameter values, such as the Type parameter, enclose the choices in curly brackets and separate them with the exclusive OR symbol(;).</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. <span data-ttu-id="3ef59-171">Si la valeur du paramètre doit utiliser une mise en forme spécifiques, tels que des guillemets ou des parenthèses, montrent le format dans la syntaxe.</span><span class="sxs-lookup"><span data-stu-id="3ef59-171">If the parameter value must use specific formatting, such as quotation marks or parentheses, show the format in the syntax.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a><span data-ttu-id="3ef59-172">Le diagramme de syntaxe XML de codage</span><span class="sxs-lookup"><span data-stu-id="3ef59-172">Coding the Syntax Diagram XML</span></span>

<span data-ttu-id="3ef59-173">Le nœud de syntaxe du code XML commence immédiatement après le nœud de description, qui se termine par le \</maml:description > balise.</span><span class="sxs-lookup"><span data-stu-id="3ef59-173">The syntax node of the XML begins immediately after the description node, which ends with the \</maml:description> tag.</span></span> <span data-ttu-id="3ef59-174">Pour plus d’informations sur la collecte des données utilisées dans le diagramme de syntaxe, consultez [collecte des informations sur la syntaxe](#Gathering-Syntax-Information).</span><span class="sxs-lookup"><span data-stu-id="3ef59-174">For information about gathering the data used in the syntax diagram, see [Gathering Syntax Information](#Gathering-Syntax-Information).</span></span>

### <a name="adding-a-syntax-node"></a><span data-ttu-id="3ef59-175">Ajout d’un nœud de syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ef59-175">Adding a Syntax Node</span></span>

<span data-ttu-id="3ef59-176">Le diagramme de syntaxe affiché dans la rubrique d’aide de l’applet de commande est généré à partir des données dans le nœud de syntaxe du document XML.</span><span class="sxs-lookup"><span data-stu-id="3ef59-176">The syntax diagram displayed in the cmdlet Help topic is generated from the data in the syntax node of the XML.</span></span> <span data-ttu-id="3ef59-177">Le nœud de syntaxe est placé dans une paire si \<: syntaxe de commande > balises.</span><span class="sxs-lookup"><span data-stu-id="3ef59-177">The syntax node is enclosed in a pair if \<command:syntax> tags.</span></span> <span data-ttu-id="3ef59-178">Avec chaque jeu de paramètres de l’applet de commande placé dans une paire de \<commande : syntaxitem > balises.</span><span class="sxs-lookup"><span data-stu-id="3ef59-178">With each parameter set of the cmdlet enclosed in a pair of \<command:syntaxitem> tags.</span></span> <span data-ttu-id="3ef59-179">Il n’existe aucune limite au nombre de \<commande : syntaxitem > balises que vous pouvez ajouter.</span><span class="sxs-lookup"><span data-stu-id="3ef59-179">There is no limit to the number of \<command:syntaxitem> tags that you can add.</span></span>

<span data-ttu-id="3ef59-180">L’exemple suivant montre un nœud de syntaxe qui possède des nœuds d’élément de syntaxe pour les deux jeux de paramètres.</span><span class="sxs-lookup"><span data-stu-id="3ef59-180">The following example shows a syntax node that has syntax item nodes for two parameter sets.</span></span>

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

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a><span data-ttu-id="3ef59-181">Ajout du nom de l’applet de commande au paramètre définie les données</span><span class="sxs-lookup"><span data-stu-id="3ef59-181">Adding the Cmdlet Name to the Parameter Set Data</span></span>

<span data-ttu-id="3ef59-182">Chaque jeu de paramètres de l’applet de commande est spécifié dans un nœud d’élément de syntaxe.</span><span class="sxs-lookup"><span data-stu-id="3ef59-182">Each parameter set of the cmdlet is specified in a syntax item node.</span></span> <span data-ttu-id="3ef59-183">Chaque nœud d’élément de syntaxe commence par une paire de \<maml:name > balises qui incluent le nom de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3ef59-183">Each syntax item node begins with a pair of \<maml:name> tags that include the name of the cmdlet.</span></span>

<span data-ttu-id="3ef59-184">L’exemple suivant inclut un nœud de syntaxe qui possède des nœuds d’élément de syntaxe pour les deux jeux de paramètres.</span><span class="sxs-lookup"><span data-stu-id="3ef59-184">The following example includes a syntax node that has syntax item nodes for two parameter sets.</span></span>

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

### <a name="adding-parameters"></a><span data-ttu-id="3ef59-185">Ajout de paramètres</span><span class="sxs-lookup"><span data-stu-id="3ef59-185">Adding Parameters</span></span>

<span data-ttu-id="3ef59-186">Chaque paramètre est ajouté au nœud d’élément de syntaxe est spécifiée au sein d’une paire de \<: paramètre de commande > balises.</span><span class="sxs-lookup"><span data-stu-id="3ef59-186">Each parameter added to the syntax item node is specified within a pair of \<command:parameter> tags.</span></span> <span data-ttu-id="3ef59-187">Vous avez besoin d’une paire de \<: paramètre de commande > balises pour chaque paramètre inclus dans le jeu de paramètres, à l’exception des paramètres courants que sont fournies par Windows PowerShell ?.</span><span class="sxs-lookup"><span data-stu-id="3ef59-187">You need a pair of \<command:parameter> tags for each parameter included in the parameter set, with the exception of the common parameters that are provided by Windows PowerShell?.</span></span>

<span data-ttu-id="3ef59-188">Les attributs de l’ouverture \<: paramètre de commande > balise déterminer comment le paramètre apparaît dans le diagramme de syntaxe.</span><span class="sxs-lookup"><span data-stu-id="3ef59-188">The attributes of the opening \<command:parameter> tag determine how the parameter appears in the syntax diagram.</span></span> <span data-ttu-id="3ef59-189">Pour plus d’informations sur les attributs de paramètre, consultez [les attributs de paramètre](#Parameter-Attributes).</span><span class="sxs-lookup"><span data-stu-id="3ef59-189">For information on parameter attributes, see [Parameter Attributes](#Parameter-Attributes).</span></span>

> [!NOTE]
> <span data-ttu-id="3ef59-190">Le \<: paramètre de commande > balise prend en charge un élément enfant \<maml:description > dont le contenu n’est jamais affiché.</span><span class="sxs-lookup"><span data-stu-id="3ef59-190">The \<command:parameter> tag supports a child element \<maml:description> whose content is never displayed.</span></span> <span data-ttu-id="3ef59-191">Les descriptions de paramètre sont spécifiées dans le nœud de paramètre du fichier XML.</span><span class="sxs-lookup"><span data-stu-id="3ef59-191">The parameter descriptions are specified in the parameter node of the XML.</span></span> <span data-ttu-id="3ef59-192">Pour éviter les incohérences entre les informations contenues dans l’élément de syntaxe plan et le nœud de paramètre, omettez la (\<maml:description > ou laissez-le vide.</span><span class="sxs-lookup"><span data-stu-id="3ef59-192">To avoid inconsistencies between the information in the syntax item bodes and the parameter node, omit the (\<maml:description> or leave it empty.</span></span>

<span data-ttu-id="3ef59-193">L’exemple suivant inclut un nœud d’élément de syntaxe pour un paramètre défini avec deux paramètres.</span><span class="sxs-lookup"><span data-stu-id="3ef59-193">The following example includes a syntax item node for a parameter set with two parameters.</span></span>

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
