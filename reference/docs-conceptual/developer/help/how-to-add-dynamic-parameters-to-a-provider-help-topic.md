---
title: Comment ajouter des paramètres dynamiques à une rubrique d’aide du fournisseur | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e20e5ad6-a6e6-4a63-9d42-1ac54214f748
caps.latest.revision: 5
ms.openlocfilehash: 59839e9b8b6f2a56f2f1a9c755f2f1a85deb34aa
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361258"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="762b1-102">Guide pratique pour ajouter des paramètres dynamiques à une rubrique d’aide de fournisseur</span><span class="sxs-lookup"><span data-stu-id="762b1-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="762b1-103">Cette section explique comment remplir la section des **paramètres dynamiques** d’une rubrique d’aide du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="762b1-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="762b1-104">Les *paramètres dynamiques* sont des paramètres d’une applet de commande ou d’une fonction qui sont disponibles uniquement dans les conditions spécifiées.</span><span class="sxs-lookup"><span data-stu-id="762b1-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="762b1-105">Les paramètres dynamiques documentés dans une rubrique d’aide du fournisseur sont les paramètres dynamiques que le fournisseur ajoute à l’applet de commande ou à la fonction lorsque l’applet de commande ou la fonction est utilisée dans le lecteur du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="762b1-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="762b1-106">Les paramètres dynamiques peuvent également être documentés dans l’aide sur les applets de commande personnalisées pour un fournisseur.</span><span class="sxs-lookup"><span data-stu-id="762b1-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="762b1-107">Lors de l’écriture de l’aide du fournisseur et de l’aide sur les applets de commande personnalisées pour un fournisseur, incluez la documentation des paramètres dynamiques dans les deux documents.</span><span class="sxs-lookup"><span data-stu-id="762b1-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span>

<span data-ttu-id="762b1-108">Si un fournisseur n’implémente aucun paramètre dynamique, la rubrique d’aide du fournisseur contient un élément `DynamicParameters` vide.</span><span class="sxs-lookup"><span data-stu-id="762b1-108">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="762b1-109">Pour ajouter des paramètres dynamiques</span><span class="sxs-lookup"><span data-stu-id="762b1-109">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="762b1-110">Dans le fichier *AssemblyName*. dll-help. xml, dans l’élément `providerHelp`, ajoutez un élément `DynamicParameters`.</span><span class="sxs-lookup"><span data-stu-id="762b1-110">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="762b1-111">L’élément `DynamicParameters` doit apparaître après l’élément `Tasks` et avant l’élément `RelatedLinks`.</span><span class="sxs-lookup"><span data-stu-id="762b1-111">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="762b1-112">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="762b1-112">For example:</span></span>

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

   <span data-ttu-id="762b1-113">Si le fournisseur n’implémente aucun paramètre dynamique, l’élément `DynamicParameters` peut être vide.</span><span class="sxs-lookup"><span data-stu-id="762b1-113">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="762b1-114">Dans l’élément `DynamicParameters`, pour chaque paramètre dynamique, ajoutez un élément `DynamicParameter`.</span><span class="sxs-lookup"><span data-stu-id="762b1-114">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="762b1-115">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="762b1-115">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="762b1-116">Dans chaque élément `DynamicParameter`, ajoutez un élément `Name` et `CmdletSupported`.</span><span class="sxs-lookup"><span data-stu-id="762b1-116">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="762b1-117">Nom de l’élément</span><span class="sxs-lookup"><span data-stu-id="762b1-117">Element Name</span></span>|<span data-ttu-id="762b1-118">Description</span><span class="sxs-lookup"><span data-stu-id="762b1-118">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="762b1-119">Name</span><span class="sxs-lookup"><span data-stu-id="762b1-119">Name</span></span>|<span data-ttu-id="762b1-120">Spécifie le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="762b1-120">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="762b1-121">CmdletSupported</span><span class="sxs-lookup"><span data-stu-id="762b1-121">CmdletSupported</span></span>|<span data-ttu-id="762b1-122">Spécifie les applets de commande dans lesquelles le paramètre est valide.</span><span class="sxs-lookup"><span data-stu-id="762b1-122">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="762b1-123">Tapez une liste séparée par des virgules de noms d’applets de commande.</span><span class="sxs-lookup"><span data-stu-id="762b1-123">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="762b1-124">Par exemple, le code XML suivant décrit le paramètre dynamique `Encoding` que le fournisseur de système de fichiers Windows PowerShell ajoute aux cmdlets `Add-Content`, `Get-Content`, `Set-Content`.</span><span class="sxs-lookup"><span data-stu-id="762b1-124">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="762b1-125">Dans chaque élément `DynamicParameter`, ajoutez un élément `Type`.</span><span class="sxs-lookup"><span data-stu-id="762b1-125">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="762b1-126">L’élément `Type` est un conteneur pour l’élément `Name` qui contient le type .NET de la valeur du paramètre dynamique.</span><span class="sxs-lookup"><span data-stu-id="762b1-126">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="762b1-127">Par exemple, le code XML suivant montre que le type .NET du paramètre dynamique `Encoding` est l’énumération [Microsoft. PowerShell. Commands. FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) .</span><span class="sxs-lookup"><span data-stu-id="762b1-127">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

5. <span data-ttu-id="762b1-128">Ajoutez l’élément `Description`, qui contient une brève description du paramètre dynamique.</span><span class="sxs-lookup"><span data-stu-id="762b1-128">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="762b1-129">Lorsque vous composez la description, utilisez les instructions prescrites pour tous les paramètres d’applet de commande dans [comment ajouter des informations de paramètres](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="762b1-129">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="762b1-130">Par exemple, le code XML suivant comprend la description du paramètre dynamique `Encoding`.</span><span class="sxs-lookup"><span data-stu-id="762b1-130">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

6. <span data-ttu-id="762b1-131">Ajoutez l’élément `PossibleValues` et ses éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="762b1-131">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="762b1-132">Ensemble, ces éléments décrivent les valeurs du paramètre dynamique.</span><span class="sxs-lookup"><span data-stu-id="762b1-132">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="762b1-133">Cet élément est conçu pour les valeurs énumérées.</span><span class="sxs-lookup"><span data-stu-id="762b1-133">This element is designed for enumerated values.</span></span> <span data-ttu-id="762b1-134">Si le paramètre dynamique ne prend pas de valeur, comme c’est le cas avec un paramètre de commutateur, ou si les valeurs ne peuvent pas être énumérées, ajoutez un élément `PossibleValues` vide.</span><span class="sxs-lookup"><span data-stu-id="762b1-134">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="762b1-135">Le tableau suivant répertorie et décrit l’élément `PossibleValues` et ses éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="762b1-135">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="762b1-136">Nom de l’élément</span><span class="sxs-lookup"><span data-stu-id="762b1-136">Element Name</span></span>|<span data-ttu-id="762b1-137">Description</span><span class="sxs-lookup"><span data-stu-id="762b1-137">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="762b1-138">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="762b1-138">PossibleValues</span></span>|<span data-ttu-id="762b1-139">Cet élément est un conteneur.</span><span class="sxs-lookup"><span data-stu-id="762b1-139">This element is a container.</span></span> <span data-ttu-id="762b1-140">Ses éléments enfants sont décrits ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="762b1-140">Its child elements are described below.</span></span> <span data-ttu-id="762b1-141">Ajoutez un élément `PossibleValues` à chaque rubrique d’aide du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="762b1-141">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="762b1-142">L’élément peut être vide.</span><span class="sxs-lookup"><span data-stu-id="762b1-142">The element can be empty.</span></span>|
   |<span data-ttu-id="762b1-143">PossibleValue</span><span class="sxs-lookup"><span data-stu-id="762b1-143">PossibleValue</span></span>|<span data-ttu-id="762b1-144">Cet élément est un conteneur.</span><span class="sxs-lookup"><span data-stu-id="762b1-144">This element is a container.</span></span> <span data-ttu-id="762b1-145">Ses éléments enfants sont décrits ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="762b1-145">Its child elements are described below.</span></span> <span data-ttu-id="762b1-146">Ajoutez un élément `PossibleValue` pour chaque valeur du paramètre dynamique.</span><span class="sxs-lookup"><span data-stu-id="762b1-146">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="762b1-147">Value</span><span class="sxs-lookup"><span data-stu-id="762b1-147">Value</span></span>|<span data-ttu-id="762b1-148">Spécifie le nom de la valeur.</span><span class="sxs-lookup"><span data-stu-id="762b1-148">Specifies the value name.</span></span>|
   |<span data-ttu-id="762b1-149">Description</span><span class="sxs-lookup"><span data-stu-id="762b1-149">Description</span></span>|<span data-ttu-id="762b1-150">Cet élément contient un élément `Para`.</span><span class="sxs-lookup"><span data-stu-id="762b1-150">This element contains a `Para` element.</span></span> <span data-ttu-id="762b1-151">Le texte de l’élément `Para` décrit la valeur nommée dans l’élément `Value`.</span><span class="sxs-lookup"><span data-stu-id="762b1-151">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="762b1-152">Par exemple, le code XML suivant montre un élément `PossibleValue` du paramètre dynamique `Encoding`.</span><span class="sxs-lookup"><span data-stu-id="762b1-152">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="762b1-153">Exemple</span><span class="sxs-lookup"><span data-stu-id="762b1-153">Example</span></span>

<span data-ttu-id="762b1-154">L’exemple suivant montre l’élément `DynamicParameters` du paramètre dynamique `Encoding`.</span><span class="sxs-lookup"><span data-stu-id="762b1-154">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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