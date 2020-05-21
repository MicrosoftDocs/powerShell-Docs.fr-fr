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
ms.openlocfilehash: 57978616f4a868b1ad260f4b557f9b699a1ef3ab
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557122"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>Guide pratique pour ajouter des paramètres dynamiques à une rubrique d’aide de fournisseur

Cette section explique comment remplir la section des **paramètres dynamiques** d’une rubrique d’aide du fournisseur.

Les *paramètres dynamiques* sont des paramètres d’une applet de commande ou d’une fonction qui sont disponibles uniquement dans les conditions spécifiées.

Les paramètres dynamiques documentés dans une rubrique d’aide du fournisseur sont les paramètres dynamiques que le fournisseur ajoute à l’applet de commande ou à la fonction lorsque l’applet de commande ou la fonction est utilisée dans le lecteur du fournisseur.

Les paramètres dynamiques peuvent également être documentés dans l’aide sur les applets de commande personnalisées pour un fournisseur. Lors de l’écriture de l’aide du fournisseur et de l’aide sur les applets de commande personnalisées pour un fournisseur, incluez la documentation des paramètres dynamiques dans les deux documents.

Si un fournisseur n’implémente aucun paramètre dynamique, la rubrique d’aide du fournisseur contient un `DynamicParameters` élément vide.

### <a name="to-add-dynamic-parameters"></a>Pour ajouter des paramètres dynamiques

1. Dans le fichier *AssemblyName*. dll-help. xml, dans l' `providerHelp` élément, ajoutez un `DynamicParameters` élément. L' `DynamicParameters` élément doit apparaître après l' `Tasks` élément et avant l' `RelatedLinks` élément.

   Par exemple :

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

   Si le fournisseur n’implémente aucun paramètre dynamique, l' `DynamicParameters` élément peut être vide.

2. Dans l' `DynamicParameters` élément, pour chaque paramètre dynamique, ajoutez un `DynamicParameter` élément.

   Par exemple :

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. Dans chaque `DynamicParameter` élément, ajoutez un `Name` `CmdletSupported` élément and.

   |Nom de l’élément|Description|
   |------------------|-----------------|
   |Nom|Spécifie le nom du paramètre.|
   |CmdletSupported|Spécifie les applets de commande dans lesquelles le paramètre est valide. Tapez une liste séparée par des virgules de noms d’applets de commande.|

   Par exemple, le code XML suivant décrit le `Encoding` paramètre dynamique que le fournisseur de système de fichiers Windows PowerShell ajoute aux `Add-Content` applets de commande, `Get-Content` , `Set-Content` .

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. Dans chaque `DynamicParameter` élément, ajoutez un `Type` élément. L' `Type` élément est un conteneur pour l' `Name` élément qui contient le type .net de la valeur du paramètre dynamique.

   Par exemple, le code XML suivant montre que le type .NET du `Encoding` paramètre dynamique est l’énumération [Microsoft. PowerShell. Commands. FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) .

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

5. Ajoutez l' `Description` élément, qui contient une brève description du paramètre dynamique. Lorsque vous composez la description, utilisez les instructions prescrites pour tous les paramètres d’applet de commande dans [comment ajouter des informations de paramètres](./how-to-add-parameter-information.md).

   Par exemple, le code XML suivant comprend la description du `Encoding` paramètre dynamique.

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

6. Ajoutez l' `PossibleValues` élément et ses éléments enfants. Ensemble, ces éléments décrivent les valeurs du paramètre dynamique. Cet élément est conçu pour les valeurs énumérées. Si le paramètre dynamique ne prend pas de valeur, comme c’est le cas avec un paramètre de commutateur, ou si les valeurs ne peuvent pas être énumérées, ajoutez un `PossibleValues` élément vide.

   Le tableau suivant répertorie et décrit l' `PossibleValues` élément et ses éléments enfants.

   |Nom de l’élément|Description|
   |------------------|-----------------|
   |PossibleValues|Cet élément est un conteneur. Ses éléments enfants sont décrits ci-dessous. Ajoutez un `PossibleValues` élément à chaque rubrique d’aide du fournisseur. L’élément peut être vide.|
   |PossibleValue|Cet élément est un conteneur. Ses éléments enfants sont décrits ci-dessous. Ajoutez un `PossibleValue` élément pour chaque valeur du paramètre dynamique.|
   |Value|Spécifie le nom de la valeur.|
   |Description|Cet élément contient un `Para` élément. Le texte dans l' `Para` élément décrit la valeur nommée dans l' `Value` élément.|

   Par exemple, le code XML suivant montre un `PossibleValue` élément du `Encoding` paramètre dynamique.

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

## <a name="example"></a>Exemple

L’exemple suivant montre l' `DynamicParameters` élément du `Encoding` paramètre dynamique.

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
