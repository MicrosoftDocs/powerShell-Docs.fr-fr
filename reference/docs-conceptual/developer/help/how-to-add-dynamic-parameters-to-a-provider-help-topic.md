---
title: Guide pratique pour ajouter des paramètres dynamiques à une rubrique d’aide de fournisseur
ms.date: 09/13/2016
ms.openlocfilehash: ddf964292ee7bf477767a2ca17c717aef84bad51
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893456"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>Guide pratique pour ajouter des paramètres dynamiques à une rubrique d’aide de fournisseur

Cette section explique comment remplir la section des **paramètres dynamiques** d’une rubrique d’aide du fournisseur.

Les *paramètres dynamiques* sont des paramètres d’une applet de commande ou d’une fonction qui sont disponibles uniquement dans les conditions spécifiées.

Les paramètres dynamiques documentés dans une rubrique d’aide du fournisseur sont les paramètres dynamiques que le fournisseur ajoute à l’applet de commande ou à la fonction lorsque l’applet de commande ou la fonction est utilisée dans le lecteur du fournisseur.

Les paramètres dynamiques peuvent également être documentés dans l’aide sur les applets de commande personnalisées pour un fournisseur. Lors de l’écriture de l’aide du fournisseur et de l’aide sur les applets de commande personnalisées pour un fournisseur, incluez la documentation des paramètres dynamiques dans les deux documents.

Si un fournisseur n’implémente aucun paramètre dynamique, la rubrique d’aide du fournisseur contient un `DynamicParameters` élément vide.

### <a name="to-add-dynamic-parameters"></a>Pour ajouter des paramètres dynamiques

1. Dans le `<AssemblyName>.dll-help.xml` fichier, dans l' `providerHelp` élément, ajoutez un `DynamicParameters` élément. L' `DynamicParameters` élément doit apparaître après l' `Tasks` élément et avant l' `RelatedLinks` élément.

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

1. Dans l' `DynamicParameters` élément, pour chaque paramètre dynamique, ajoutez un `DynamicParameter` élément.

   Par exemple :

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

1. Dans chaque `DynamicParameter` élément, ajoutez un `Name` `CmdletSupported` élément and.

   - Nom : spécifie le nom du paramètre
   - CmdletSupported : spécifie les applets de commande dans lesquelles le paramètre est valide. Tapez une liste séparée par des virgules de noms d’applets de commande.

   Par exemple, le code XML suivant décrit le `Encoding` paramètre dynamique que le fournisseur de système de fichiers Windows PowerShell ajoute aux `Add-Content` applets de commande, `Get-Content` , `Set-Content` .

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

1. Dans chaque `DynamicParameter` élément, ajoutez un `Type` élément. L' `Type` élément est un conteneur pour l' `Name` élément qui contient le type .net de la valeur du paramètre dynamique.

   Par exemple, le code XML suivant montre que le type .NET du `Encoding` paramètre dynamique est l’énumération [FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) .

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

1. Ajoutez l' `Description` élément, qui contient une brève description du paramètre dynamique. Lorsque vous composez la description, utilisez les instructions prescrites pour tous les paramètres d’applet de commande dans [comment ajouter des informations de paramètres](./how-to-add-parameter-information.md).

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

1. Ajoutez l' `PossibleValues` élément et ses éléments enfants. Ensemble, ces éléments décrivent les valeurs du paramètre dynamique. Cet élément est conçu pour les valeurs énumérées. Si le paramètre dynamique ne prend pas de valeur, comme c’est le cas avec un paramètre de commutateur, ou si les valeurs ne peuvent pas être énumérées, ajoutez un `PossibleValues` élément vide.

   Le tableau suivant répertorie et décrit l' `PossibleValues` élément et ses éléments enfants.

   - PossibleValues : cet élément est un conteneur. Ses éléments enfants sont décrits ci-dessous. Ajoutez un `PossibleValues` élément à chaque rubrique d’aide du fournisseur. L’élément peut être vide.
   - PossibleValue : cet élément est un conteneur. Ses éléments enfants sont décrits ci-dessous. Ajoutez un `PossibleValue` élément pour chaque valeur du paramètre dynamique.
   - Valeur : spécifie le nom de la valeur.
   - Description : cet élément contient un `Para` élément. Le texte dans l' `Para` élément décrit la valeur nommée dans l' `Value` élément.

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
