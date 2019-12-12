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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361258"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>Guide pratique pour ajouter des paramètres dynamiques à une rubrique d’aide de fournisseur

Cette section explique comment remplir la section des **paramètres dynamiques** d’une rubrique d’aide du fournisseur.

Les *paramètres dynamiques* sont des paramètres d’une applet de commande ou d’une fonction qui sont disponibles uniquement dans les conditions spécifiées.

Les paramètres dynamiques documentés dans une rubrique d’aide du fournisseur sont les paramètres dynamiques que le fournisseur ajoute à l’applet de commande ou à la fonction lorsque l’applet de commande ou la fonction est utilisée dans le lecteur du fournisseur.

Les paramètres dynamiques peuvent également être documentés dans l’aide sur les applets de commande personnalisées pour un fournisseur. Lors de l’écriture de l’aide du fournisseur et de l’aide sur les applets de commande personnalisées pour un fournisseur, incluez la documentation des paramètres dynamiques dans les deux documents.

Si un fournisseur n’implémente aucun paramètre dynamique, la rubrique d’aide du fournisseur contient un élément `DynamicParameters` vide.

### <a name="to-add-dynamic-parameters"></a>Pour ajouter des paramètres dynamiques

1. Dans le fichier *AssemblyName*. dll-help. xml, dans l’élément `providerHelp`, ajoutez un élément `DynamicParameters`. L’élément `DynamicParameters` doit apparaître après l’élément `Tasks` et avant l’élément `RelatedLinks`.

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

   Si le fournisseur n’implémente aucun paramètre dynamique, l’élément `DynamicParameters` peut être vide.

2. Dans l’élément `DynamicParameters`, pour chaque paramètre dynamique, ajoutez un élément `DynamicParameter`.

   Par exemple :

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. Dans chaque élément `DynamicParameter`, ajoutez un `Name` et un élément `CmdletSupported`.

   |Nom de l’élément|Description|
   |------------------|-----------------|
   |Name|Spécifie le nom du paramètre.|
   |CmdletSupported|Spécifie les applets de commande dans lesquelles le paramètre est valide. Tapez une liste séparée par des virgules de noms d’applets de commande.|

   Par exemple, le code XML suivant décrit le `Encoding` paramètre dynamique que le fournisseur de système de fichiers Windows PowerShell ajoute aux applets de commande `Add-Content`, `Get-Content``Set-Content`.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. Dans chaque élément `DynamicParameter`, ajoutez un élément `Type`. L’élément `Type` est un conteneur pour l’élément `Name` qui contient le type .NET de la valeur du paramètre dynamique.

   Par exemple, le code XML suivant montre que le type .NET de l' `Encoding` paramètre dynamique est l’énumération [Microsoft. PowerShell. Commands. FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) .

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

5. Ajoutez l’élément `Description`, qui contient une brève description du paramètre dynamique. Lorsque vous composez la description, utilisez les instructions prescrites pour tous les paramètres d’applet de commande dans [comment ajouter des informations de paramètres](./how-to-add-parameter-information.md).

   Par exemple, le code XML suivant comprend la description du paramètre dynamique `Encoding`.

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

6. Ajoutez l’élément `PossibleValues` et ses éléments enfants. Ensemble, ces éléments décrivent les valeurs du paramètre dynamique. Cet élément est conçu pour les valeurs énumérées. Si le paramètre dynamique ne prend pas de valeur, comme c’est le cas avec un paramètre de commutateur, ou si les valeurs ne peuvent pas être énumérées, ajoutez un élément `PossibleValues` vide.

   Le tableau suivant répertorie et décrit l’élément `PossibleValues` et ses éléments enfants.

   |Nom de l’élément|Description|
   |------------------|-----------------|
   |PossibleValues|Cet élément est un conteneur. Ses éléments enfants sont décrits ci-dessous. Ajoutez un élément `PossibleValues` à chaque rubrique d’aide du fournisseur. L’élément peut être vide.|
   |PossibleValue|Cet élément est un conteneur. Ses éléments enfants sont décrits ci-dessous. Ajoutez un élément `PossibleValue` pour chaque valeur du paramètre dynamique.|
   |Value|Spécifie le nom de la valeur.|
   |Description|Cet élément contient un élément `Para`. Le texte de l’élément `Para` décrit la valeur nommée dans l’élément `Value`.|

   Par exemple, le code XML suivant montre un élément `PossibleValue` du paramètre dynamique `Encoding`.

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

L’exemple suivant montre l’élément `DynamicParameters` du paramètre dynamique `Encoding`.

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