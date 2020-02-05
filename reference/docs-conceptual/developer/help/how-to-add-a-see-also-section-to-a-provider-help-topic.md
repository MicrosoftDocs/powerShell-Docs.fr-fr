---
title: Comment ajouter une section Voir aussi à une rubrique d’aide du fournisseur | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: 1c1b7f4cf56ea2f9e30438a60e7bee29d87b80ba
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995951"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a>Guide pratique pour une section Voir aussi à une rubrique d’aide de fournisseur

Cette section explique comment remplir la section **Voir aussi** d’une rubrique d’aide du fournisseur.

La section **Voir aussi** est constituée d’une liste de rubriques relatives au fournisseur ou qui peut aider l’utilisateur à mieux comprendre et à utiliser le fournisseur. La liste de rubriques peut inclure des rubriques d’aide sur les applets de commande, aide du fournisseur et concepts (« à propos de ») dans Windows PowerShell. Il peut également inclure des références à des livres, des documents et des rubriques en ligne, notamment une version en ligne de la rubrique d’aide actuelle du fournisseur.

Lorsque vous faites référence à des rubriques en ligne, fournissez l’URI ou un terme de recherche en texte brut. L’applet de commande `Get-Help` n’effectue pas de liaison ou de redirection vers l’une des rubriques de la liste. En outre, le paramètre `Online` de l’applet de commande `Get-Help` ne fonctionne pas avec l’aide du fournisseur.

La section Voir aussi est créée à partir de l’élément `RelatedLinks` et des balises qu’elle contient. Le code XML suivant montre comment ajouter les balises.

### <a name="to-add-see-also-topics"></a>Pour ajouter des rubriques « Voir aussi »

1. Dans le fichier *AssemblyName*. dll-help. xml, dans l’élément `providerHelp`, ajoutez un élément `RelatedLinks`. L’élément `RelatedLinks` doit être le dernier élément de l’élément `providerHelp`. Un seul élément `RelatedLinks` est autorisé dans chaque rubrique d’aide du fournisseur.

   Par exemple :

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. Pour chaque rubrique de la section **Voir aussi** , dans l’élément `RelatedLinks`, ajoutez un élément `navigationLink`. Ensuite, dans chaque élément `navigationLink`, ajoutez un élément `linkText` et un élément `uri`. Si vous n’utilisez pas l’élément `uri`, vous pouvez l’ajouter en tant qu’élément vide (\<URI/>).

   Par exemple :

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

3. Tapez le nom de la rubrique entre les balises `linkText`. Si vous fournissez un URI, tapez-le entre les balises `uri`. Pour indiquer la version en ligne de la rubrique d’aide actuelle du fournisseur, entre les balises `linkText`, tapez « version en ligne : » à la place du nom de la rubrique. En règle générale, le lien « version en ligne : » est la première rubrique de la liste de rubriques Voir aussi.

   L’exemple suivant inclut trois rubriques Voir aussi. La première référence à la version en ligne de la rubrique active. Le deuxième fait référence à une rubrique d’aide sur les applets de commande Windows PowerShell. Le troisième fait référence à une autre rubrique en ligne.

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
                <uri>https://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```