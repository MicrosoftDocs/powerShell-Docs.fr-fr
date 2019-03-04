---
title: Comment ajouter un, consultez Section une rubrique d’aide de fournisseur | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858345"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a>Guide pratique pour une section Voir aussi à une rubrique d’aide de fournisseur

Cette section explique comment remplir le **Voir aussi** section d’une rubrique d’aide de fournisseur.

Le **Voir aussi** section se compose d’une liste de rubriques qui sont liées au fournisseur ou peut aider l’utilisateur à mieux comprendre et utiliser le fournisseur. La liste de rubriques peut inclure l’aide de l’applet de commande, fournisseur aide et conceptuelles (« about ») des rubriques d’aide dans Windows PowerShell. Il peut également inclure des références à la documentation, papier et rubriques en ligne, y compris une version en ligne de la rubrique d’aide fournisseur actuel.

Lorsque vous faites référence à des rubriques en ligne, indiquez l’URI ou un terme de recherche en texte brut. Le `Get-Help` applet de commande ne pas lier ou rediriger vers les rubriques dans la liste. En outre, le `Online` paramètre de la `Get-Help` applet de commande ne fonctionne pas avec l’aide du fournisseur.

La section Voir aussi est créée à partir du `RelatedLinks` élément les balises et qu’il contient. Le code XML suivant montre comment ajouter des balises.

### <a name="to-add-see-also-topics"></a>Pour ajouter des rubriques « Voir aussi »

1. Dans le *AssemblyName*.dll-help.xml de fichiers, dans le `providerHelp` élément, ajoutez un `RelatedLinks` élément. Le `RelatedLinks` élément doit être le dernier élément dans le `providerHelp` élément. Seul `RelatedLinks` élément est autorisé dans chaque rubrique d’aide de fournisseur.

   Par exemple :

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. Pour chaque rubrique de la **Voir aussi** section dans le `RelatedLinks` élément, ajoutez un `navigationLink` élément. Ensuite, dans chaque `navigationLink` élément, ajouter un `linkText` et un élément `uri` élément. Si vous n’utilisez pas le `uri` élément, vous pouvez l’ajouter comme un élément vide (\<uri / >).

   Par exemple :

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> </linkText>
                <uri> </uri>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```

3. Tapez le nom de rubrique entre le `linkText` balises. Si vous fournissez un URI, tapez-le entre le `uri` balises. Pour indiquer la version en ligne de la rubrique d’aide fournisseur actuel, entre le `linkText` balises, tapez « version en ligne : « au lieu du nom de la rubrique. En règle générale, la « version en ligne : « lien est la première rubrique dans la liste de rubrique Voir aussi.

   L’exemple suivant inclut les trois rubriques connexes. Le premier font référence à la version en ligne de la rubrique active. Le second fait référence à une rubrique d’aide applet de commande Windows PowerShell. Le troisième fait référence à une autre rubrique en ligne.

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> Online version: </linkText>
                <uri>http://www.fabrikam.com/help/myFunction.htm</uri>
            </navigationLink>
            <navigationLink>
                <linkText> about_functions </linkText>
                <uri/>
            </navigationLink>
            <navigationLink>
                <linkText> Windows PowerShell Getting Started Guide </linkText>
                <uri>http://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```