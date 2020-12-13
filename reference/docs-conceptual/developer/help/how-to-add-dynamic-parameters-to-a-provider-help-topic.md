---
ms.date: 09/13/2016
ms.topic: reference
title: Guide pratique pour ajouter des paramètres dynamiques à une rubrique d’aide de fournisseur
description: Guide pratique pour ajouter des paramètres dynamiques à une rubrique d’aide de fournisseur
ms.openlocfilehash: 9542538cfacf5fb293ca8d1350b80fb250c71ac6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649642"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="6d0d4-103">Guide pratique pour ajouter des paramètres dynamiques à une rubrique d’aide de fournisseur</span><span class="sxs-lookup"><span data-stu-id="6d0d4-103">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="6d0d4-104">Cette section explique comment remplir la section des **paramètres dynamiques** d’une rubrique d’aide du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-104">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="6d0d4-105">Les *paramètres dynamiques* sont des paramètres d’une applet de commande ou d’une fonction qui sont disponibles uniquement dans les conditions spécifiées.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-105">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="6d0d4-106">Les paramètres dynamiques documentés dans une rubrique d’aide du fournisseur sont les paramètres dynamiques que le fournisseur ajoute à l’applet de commande ou à la fonction lorsque l’applet de commande ou la fonction est utilisée dans le lecteur du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-106">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="6d0d4-107">Les paramètres dynamiques peuvent également être documentés dans l’aide sur les applets de commande personnalisées pour un fournisseur.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-107">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="6d0d4-108">Lors de l’écriture de l’aide du fournisseur et de l’aide sur les applets de commande personnalisées pour un fournisseur, incluez la documentation des paramètres dynamiques dans les deux documents.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-108">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span>

<span data-ttu-id="6d0d4-109">Si un fournisseur n’implémente aucun paramètre dynamique, la rubrique d’aide du fournisseur contient un `DynamicParameters` élément vide.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-109">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="6d0d4-110">Pour ajouter des paramètres dynamiques</span><span class="sxs-lookup"><span data-stu-id="6d0d4-110">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="6d0d4-111">Dans le `<AssemblyName>.dll-help.xml` fichier, dans l' `providerHelp` élément, ajoutez un `DynamicParameters` élément.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-111">In the `<AssemblyName>.dll-help.xml` file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="6d0d4-112">L' `DynamicParameters` élément doit apparaître après l' `Tasks` élément et avant l' `RelatedLinks` élément.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-112">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="6d0d4-113">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="6d0d4-113">For example:</span></span>

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

   <span data-ttu-id="6d0d4-114">Si le fournisseur n’implémente aucun paramètre dynamique, l' `DynamicParameters` élément peut être vide.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-114">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

1. <span data-ttu-id="6d0d4-115">Dans l' `DynamicParameters` élément, pour chaque paramètre dynamique, ajoutez un `DynamicParameter` élément.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-115">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="6d0d4-116">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="6d0d4-116">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

1. <span data-ttu-id="6d0d4-117">Dans chaque `DynamicParameter` élément, ajoutez un `Name` `CmdletSupported` élément and.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-117">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   - <span data-ttu-id="6d0d4-118">Nom : spécifie le nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="6d0d4-118">Name - Specifies the parameter name</span></span>
   - <span data-ttu-id="6d0d4-119">CmdletSupported : spécifie les applets de commande dans lesquelles le paramètre est valide.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-119">CmdletSupported - Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="6d0d4-120">Tapez une liste séparée par des virgules de noms d’applets de commande.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-120">Type a comma-separated list of cmdlet names.</span></span>

   <span data-ttu-id="6d0d4-121">Par exemple, le code XML suivant décrit le `Encoding` paramètre dynamique que le fournisseur de système de fichiers Windows PowerShell ajoute aux `Add-Content` applets de commande, `Get-Content` , `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="6d0d4-121">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

1. <span data-ttu-id="6d0d4-122">Dans chaque `DynamicParameter` élément, ajoutez un `Type` élément.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-122">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="6d0d4-123">L' `Type` élément est un conteneur pour l' `Name` élément qui contient le type .net de la valeur du paramètre dynamique.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-123">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="6d0d4-124">Par exemple, le code XML suivant montre que le type .NET du `Encoding` paramètre dynamique est l’énumération [FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) .</span><span class="sxs-lookup"><span data-stu-id="6d0d4-124">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

1. <span data-ttu-id="6d0d4-125">Ajoutez l' `Description` élément, qui contient une brève description du paramètre dynamique.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-125">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="6d0d4-126">Lorsque vous composez la description, utilisez les instructions prescrites pour tous les paramètres d’applet de commande dans [comment ajouter des informations de paramètres](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="6d0d4-126">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="6d0d4-127">Par exemple, le code XML suivant comprend la description du `Encoding` paramètre dynamique.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-127">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

1. <span data-ttu-id="6d0d4-128">Ajoutez l' `PossibleValues` élément et ses éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-128">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="6d0d4-129">Ensemble, ces éléments décrivent les valeurs du paramètre dynamique.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-129">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="6d0d4-130">Cet élément est conçu pour les valeurs énumérées.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-130">This element is designed for enumerated values.</span></span> <span data-ttu-id="6d0d4-131">Si le paramètre dynamique ne prend pas de valeur, comme c’est le cas avec un paramètre de commutateur, ou si les valeurs ne peuvent pas être énumérées, ajoutez un `PossibleValues` élément vide.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-131">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="6d0d4-132">Le tableau suivant répertorie et décrit l' `PossibleValues` élément et ses éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-132">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   - <span data-ttu-id="6d0d4-133">PossibleValues : cet élément est un conteneur.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-133">PossibleValues - This element is a container.</span></span> <span data-ttu-id="6d0d4-134">Ses éléments enfants sont décrits ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-134">Its child elements are described below.</span></span> <span data-ttu-id="6d0d4-135">Ajoutez un `PossibleValues` élément à chaque rubrique d’aide du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-135">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="6d0d4-136">L’élément peut être vide.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-136">The element can be empty.</span></span>
   - <span data-ttu-id="6d0d4-137">PossibleValue : cet élément est un conteneur.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-137">PossibleValue - This element is a container.</span></span> <span data-ttu-id="6d0d4-138">Ses éléments enfants sont décrits ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-138">Its child elements are described below.</span></span> <span data-ttu-id="6d0d4-139">Ajoutez un `PossibleValue` élément pour chaque valeur du paramètre dynamique.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-139">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>
   - <span data-ttu-id="6d0d4-140">Valeur : spécifie le nom de la valeur.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-140">Value - Specifies the value name.</span></span>
   - <span data-ttu-id="6d0d4-141">Description : cet élément contient un `Para` élément.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-141">Description - This element contains a `Para` element.</span></span> <span data-ttu-id="6d0d4-142">Le texte dans l' `Para` élément décrit la valeur nommée dans l' `Value` élément.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-142">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>

   <span data-ttu-id="6d0d4-143">Par exemple, le code XML suivant montre un `PossibleValue` élément du `Encoding` paramètre dynamique.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-143">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="6d0d4-144">Exemple</span><span class="sxs-lookup"><span data-stu-id="6d0d4-144">Example</span></span>

<span data-ttu-id="6d0d4-145">L’exemple suivant montre l' `DynamicParameters` élément du `Encoding` paramètre dynamique.</span><span class="sxs-lookup"><span data-stu-id="6d0d4-145">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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
