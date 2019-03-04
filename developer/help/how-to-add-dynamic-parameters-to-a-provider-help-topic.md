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
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>Guide pratique pour ajouter des paramètres dynamiques à une rubrique d’aide de fournisseur

Cette section explique comment remplir le **paramètres dynamiques** section d’une rubrique d’aide de fournisseur.

*Les paramètres dynamiques* sont des paramètres d’applet de commande ou fonction qui sont disponibles uniquement sous les conditions spécifiées.

Les paramètres dynamiques sont documentées dans une rubrique d’aide de fournisseur sont les paramètres dynamiques que le fournisseur ajoute à l’applet de commande ou de la fonction lorsque l’applet de commande ou la fonction est utilisée dans le lecteur fournisseur.

Les paramètres dynamiques peuvent également être documentés dans l’aide de l’applet de commande personnalisée pour un fournisseur. Lorsque vous écrivez l’aide du fournisseur et aide de l’applet de commande personnalisée pour un fournisseur, inclure la documentation de paramètre dynamique dans les deux documents. Pour plus d’informations sur l’aide de l’applet de commande personnalisée, consultez [écriture Windows PowerShell applet de commande aide personnalisée pour les fournisseurs](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).

Si un fournisseur n’implémente pas aucun paramètre dynamique, la rubrique d’aide fournisseur contient vide `DynamicParameters` élément.

### <a name="to-add-dynamic-parameters"></a>Pour ajouter des paramètres dynamiques

1. Dans le *AssemblyName*.dll-help.xml de fichiers, dans le `providerHelp` élément, ajoutez un `DynamicParameters` élément. Le `DynamicParameters` élément doit apparaître après le `Tasks` élément et avant la `RelatedLinks` élément.

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

   Si le fournisseur n’implémente pas aucun paramètre dynamique, le `DynamicParameters` élément peut être vide.

2. Dans le `DynamicParameters` élément, pour chaque paramètre dynamique, ajoutez un `DynamicParameter` élément.

   Par exemple :

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. Dans chaque `DynamicParameter` élément, ajoutez un `Name` et `CmdletSupported` élément.

   |Nom de l’élément|Description|
   |------------------|-----------------|
   |Name|Spécifie le nom du paramètre.|
   |CmdletSupported|Spécifie les applets de commande dans laquelle le paramètre est valide. Tapez une liste séparée par des virgules des noms d’applet de commande.|

   Par exemple, les documents XML suivants le `Encoding` paramètre dynamique que le fournisseur FileSystem de Windows PowerShell ajoute à la `Add-Content`, `Get-Content`, `Set-Content` applets de commande.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. Dans chaque `DynamicParameter` élément, ajoutez un `Type` élément. Le `Type` élément est un conteneur pour le `Name` élément qui contient le type .NET de la valeur du paramètre dynamique.

   Par exemple, le code XML suivant montre que le type .NET de la `Encoding` paramètre dynamique est la [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) énumération.

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

5. Ajouter le `Description` élément, qui contient une brève description du paramètre dynamique. Lorsque vous composez la description, utilisez les instructions prescrites pour tous les paramètres d’applet de commande dans [comment ajouter des informations de paramètre](./how-to-add-parameter-information.md).

   Par exemple, le code XML suivant contient la description de le `Encoding` paramètre dynamique.

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

6. Ajouter le `PossibleValues` élément et ses éléments enfants. Ensemble, ces éléments décrivent les valeurs du paramètre dynamique. Cet élément est conçu pour les valeurs énumérées. Si le paramètre dynamique ne prend pas de valeur, comme c’est le cas avec un paramètre de commutateur ou les valeurs ne peuvent pas être énumérés, ajoutez vide `PossibleValues` élément.

   Le tableau suivant répertorie et décrit les `PossibleValues` élément et ses éléments enfants.

   |Nom de l’élément|Description|
   |------------------|-----------------|
   |PossibleValues|Cet élément est un conteneur. Ses éléments enfants sont décrits ci-dessous. Ajouter un `PossibleValues` élément à chaque rubrique d’aide de fournisseur. L’élément peut être vide.|
   |PossibleValue|Cet élément est un conteneur. Ses éléments enfants sont décrits ci-dessous. Ajouter un `PossibleValue` élément pour chaque valeur du paramètre dynamique.|
   |Valeur|Spécifie le nom de valeur.|
   |Description|Cet élément contient un `Para` élément. Le texte dans le `Para` élément décrit la valeur qui est nommée dans le `Value` élément.|

   Par exemple, le code XML suivant montre une `PossibleValue` élément de la `Encoding` paramètre dynamique.

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

L’exemple suivant montre le `DynamicParameters` élément de la `Encoding` paramètre dynamique.

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