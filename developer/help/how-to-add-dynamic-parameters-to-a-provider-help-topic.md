---
title: Comment ajouter des paramètres dynamiques à une rubrique d’aide de fournisseur | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e20e5ad6-a6e6-4a63-9d42-1ac54214f748
caps.latest.revision: 5
ms.openlocfilehash: cc4877242a16a9caa99564aeaae985f85e38791e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859875"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="c85d5-102">Guide pratique pour ajouter des paramètres dynamiques à une rubrique d’aide de fournisseur</span><span class="sxs-lookup"><span data-stu-id="c85d5-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="c85d5-103">Cette section explique comment remplir le **paramètres dynamiques** section d’une rubrique d’aide de fournisseur.</span><span class="sxs-lookup"><span data-stu-id="c85d5-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="c85d5-104">*Les paramètres dynamiques* sont des paramètres d’applet de commande ou fonction qui sont disponibles uniquement sous les conditions spécifiées.</span><span class="sxs-lookup"><span data-stu-id="c85d5-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="c85d5-105">Les paramètres dynamiques sont documentées dans une rubrique d’aide de fournisseur sont les paramètres dynamiques que le fournisseur ajoute à l’applet de commande ou de la fonction lorsque l’applet de commande ou la fonction est utilisée dans le lecteur fournisseur.</span><span class="sxs-lookup"><span data-stu-id="c85d5-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="c85d5-106">Les paramètres dynamiques peuvent également être documentés dans l’aide de l’applet de commande personnalisée pour un fournisseur.</span><span class="sxs-lookup"><span data-stu-id="c85d5-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="c85d5-107">Lorsque vous écrivez l’aide du fournisseur et aide de l’applet de commande personnalisée pour un fournisseur, inclure la documentation de paramètre dynamique dans les deux documents.</span><span class="sxs-lookup"><span data-stu-id="c85d5-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span> <span data-ttu-id="c85d5-108">Pour plus d’informations sur l’aide de l’applet de commande personnalisée, consultez [écriture Windows PowerShell applet de commande aide personnalisée pour les fournisseurs](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span><span class="sxs-lookup"><span data-stu-id="c85d5-108">For more information about custom cmdlet help, see [Writing Windows PowerShell Custom Cmdlet Help for Providers](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span></span>

<span data-ttu-id="c85d5-109">Si un fournisseur n’implémente pas aucun paramètre dynamique, la rubrique d’aide fournisseur contient vide `DynamicParameters` élément.</span><span class="sxs-lookup"><span data-stu-id="c85d5-109">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="c85d5-110">Pour ajouter des paramètres dynamiques</span><span class="sxs-lookup"><span data-stu-id="c85d5-110">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="c85d5-111">Dans le *AssemblyName*.dll-help.xml de fichiers, dans le `providerHelp` élément, ajoutez un `DynamicParameters` élément.</span><span class="sxs-lookup"><span data-stu-id="c85d5-111">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="c85d5-112">Le `DynamicParameters` élément doit apparaître après le `Tasks` élément et avant la `RelatedLinks` élément.</span><span class="sxs-lookup"><span data-stu-id="c85d5-112">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="c85d5-113">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c85d5-113">For example:</span></span>

    ```xml
    <providerHelp>
        <Tasks>
        </Tasks>
        <DynamicParameters>
        </DynamicParameters>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

   <span data-ttu-id="c85d5-114">Si le fournisseur n’implémente pas aucun paramètre dynamique, le `DynamicParameters` élément peut être vide.</span><span class="sxs-lookup"><span data-stu-id="c85d5-114">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="c85d5-115">Dans le `DynamicParameters` élément, pour chaque paramètre dynamique, ajoutez un `DynamicParameter` élément.</span><span class="sxs-lookup"><span data-stu-id="c85d5-115">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="c85d5-116">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c85d5-116">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="c85d5-117">Dans chaque `DynamicParameter` élément, ajoutez un `Name` et `CmdletSupported` élément.</span><span class="sxs-lookup"><span data-stu-id="c85d5-117">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="c85d5-118">Nom de l’élément</span><span class="sxs-lookup"><span data-stu-id="c85d5-118">Element Name</span></span>|<span data-ttu-id="c85d5-119">Description</span><span class="sxs-lookup"><span data-stu-id="c85d5-119">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="c85d5-120">Name</span><span class="sxs-lookup"><span data-stu-id="c85d5-120">Name</span></span>|<span data-ttu-id="c85d5-121">Spécifie le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="c85d5-121">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="c85d5-122">CmdletSupported</span><span class="sxs-lookup"><span data-stu-id="c85d5-122">CmdletSupported</span></span>|<span data-ttu-id="c85d5-123">Spécifie les applets de commande dans laquelle le paramètre est valide.</span><span class="sxs-lookup"><span data-stu-id="c85d5-123">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="c85d5-124">Tapez une liste séparée par des virgules des noms d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c85d5-124">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="c85d5-125">Par exemple, les documents XML suivants le `Encoding` paramètre dynamique que le fournisseur FileSystem de Windows PowerShell ajoute à la `Add-Content`, `Get-Content`, `Set-Content` applets de commande.</span><span class="sxs-lookup"><span data-stu-id="c85d5-125">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="c85d5-126">Dans chaque `DynamicParameter` élément, ajoutez un `Type` élément.</span><span class="sxs-lookup"><span data-stu-id="c85d5-126">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="c85d5-127">Le `Type` élément est un conteneur pour le `Name` élément qui contient le type .NET de la valeur du paramètre dynamique.</span><span class="sxs-lookup"><span data-stu-id="c85d5-127">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="c85d5-128">Par exemple, le code XML suivant montre que le type .NET de la `Encoding` paramètre dynamique est la [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) énumération.</span><span class="sxs-lookup"><span data-stu-id="c85d5-128">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
    ...
    </DynamicParameters>
    ```

5. <span data-ttu-id="c85d5-129">Ajouter le `Description` élément, qui contient une brève description du paramètre dynamique.</span><span class="sxs-lookup"><span data-stu-id="c85d5-129">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="c85d5-130">Lorsque vous composez la description, utilisez les instructions prescrites pour tous les paramètres d’applet de commande dans [comment ajouter des informations de paramètre](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="c85d5-130">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="c85d5-131">Par exemple, le code XML suivant contient la description de le `Encoding` paramètre dynamique.</span><span class="sxs-lookup"><span data-stu-id="c85d5-131">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
            <Description> Specifies the encoding of the output file that contains the content. </Description>
    ...
    </DynamicParameters>
    ```

6. <span data-ttu-id="c85d5-132">Ajouter le `PossibleValues` élément et ses éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="c85d5-132">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="c85d5-133">Ensemble, ces éléments décrivent les valeurs du paramètre dynamique.</span><span class="sxs-lookup"><span data-stu-id="c85d5-133">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="c85d5-134">Cet élément est conçu pour les valeurs énumérées.</span><span class="sxs-lookup"><span data-stu-id="c85d5-134">This element is designed for enumerated values.</span></span> <span data-ttu-id="c85d5-135">Si le paramètre dynamique ne prend pas de valeur, comme c’est le cas avec un paramètre de commutateur ou les valeurs ne peuvent pas être énumérés, ajoutez vide `PossibleValues` élément.</span><span class="sxs-lookup"><span data-stu-id="c85d5-135">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="c85d5-136">Le tableau suivant répertorie et décrit les `PossibleValues` élément et ses éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="c85d5-136">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="c85d5-137">Nom de l’élément</span><span class="sxs-lookup"><span data-stu-id="c85d5-137">Element Name</span></span>|<span data-ttu-id="c85d5-138">Description</span><span class="sxs-lookup"><span data-stu-id="c85d5-138">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="c85d5-139">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="c85d5-139">PossibleValues</span></span>|<span data-ttu-id="c85d5-140">Cet élément est un conteneur.</span><span class="sxs-lookup"><span data-stu-id="c85d5-140">This element is a container.</span></span> <span data-ttu-id="c85d5-141">Ses éléments enfants sont décrits ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="c85d5-141">Its child elements are described below.</span></span> <span data-ttu-id="c85d5-142">Ajouter un `PossibleValues` élément à chaque rubrique d’aide de fournisseur.</span><span class="sxs-lookup"><span data-stu-id="c85d5-142">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="c85d5-143">L’élément peut être vide.</span><span class="sxs-lookup"><span data-stu-id="c85d5-143">The element can be empty.</span></span>|
   |<span data-ttu-id="c85d5-144">PossibleValue</span><span class="sxs-lookup"><span data-stu-id="c85d5-144">PossibleValue</span></span>|<span data-ttu-id="c85d5-145">Cet élément est un conteneur.</span><span class="sxs-lookup"><span data-stu-id="c85d5-145">This element is a container.</span></span> <span data-ttu-id="c85d5-146">Ses éléments enfants sont décrits ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="c85d5-146">Its child elements are described below.</span></span> <span data-ttu-id="c85d5-147">Ajouter un `PossibleValue` élément pour chaque valeur du paramètre dynamique.</span><span class="sxs-lookup"><span data-stu-id="c85d5-147">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="c85d5-148">Valeur</span><span class="sxs-lookup"><span data-stu-id="c85d5-148">Value</span></span>|<span data-ttu-id="c85d5-149">Spécifie le nom de valeur.</span><span class="sxs-lookup"><span data-stu-id="c85d5-149">Specifies the value name.</span></span>|
   |<span data-ttu-id="c85d5-150">Description</span><span class="sxs-lookup"><span data-stu-id="c85d5-150">Description</span></span>|<span data-ttu-id="c85d5-151">Cet élément contient un `Para` élément.</span><span class="sxs-lookup"><span data-stu-id="c85d5-151">This element contains a `Para` element.</span></span> <span data-ttu-id="c85d5-152">Le texte dans le `Para` élément décrit la valeur qui est nommée dans le `Value` élément.</span><span class="sxs-lookup"><span data-stu-id="c85d5-152">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="c85d5-153">Par exemple, le code XML suivant montre une `PossibleValue` élément de la `Encoding` paramètre dynamique.</span><span class="sxs-lookup"><span data-stu-id="c85d5-153">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
    ...
            <Description> Specifies the encoding of the output file that contains the content. </Description>
            <PossibleValues>
                <PossibleValue>
                    <Value> ASCII </Value>
                    <Description>
                        <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                    </Description>
                </PossibleValue>
    ...
            </PossibleValues>
    </DynamicParameters>
    ```

## <a name="example"></a><span data-ttu-id="c85d5-154">Exemple</span><span class="sxs-lookup"><span data-stu-id="c85d5-154">Example</span></span>

<span data-ttu-id="c85d5-155">L’exemple suivant montre le `DynamicParameters` élément de la `Encoding` paramètre dynamique.</span><span class="sxs-lookup"><span data-stu-id="c85d5-155">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

```xml
<DynamicParameters/>
    <DynamicParameter>
        <Name> Encoding </Name>
        <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
        <Type>
            <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
        <Type>
        <Description> Specifies the encoding of the output file that contains the content. </Description>
        <PossibleValues>
            <PossibleValue>
                <Value> ASCII </Value>
                <Description>
                    <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                </Description>
            </PossibleValue>
            <PossibleValue>
                <Value> Unicode </Value>
                <Description>
                    <para> Encodes in UTF-16 format using the little-endian byte order. </para>
                </Description>
            </PossibleValue>
        </PossibleValues>
</DynamicParameters>
```