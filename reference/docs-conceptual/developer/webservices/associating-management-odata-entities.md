---
title: Association d’entités de gestion OData | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 947a3add-3593-400d-8144-8b44c8adbe5e
caps.latest.revision: 5
ms.openlocfilehash: 4849735bf412497f5590b109c67760b6a197cb2b
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83561726"
---
# <a name="associating-management-odata-entities"></a>Association d’entités Management OData

Il est souvent utile de créer une association entre deux entités OData de gestion. Par exemple, un service OData de gestion peut avoir des entités qui gèrent un catalogue de produits organisés en catégories, et qui définissent les entités `Product` et `Category` . En associant ces deux entités, un client peut obtenir des informations sur tous les produits d’une catégorie avec une seule demande au service Web.

Un exemple qui montre comment créer des associations entre des entités peut être téléchargé à l' [exemple Association](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).

## <a name="creating-the-association-in-the-resource-schema-file"></a>Création de l’Association dans le fichier de schéma de ressource

Le fichier MOF suivant définit deux entités. Nous allons créer une association entre eux.

```csharp
class Product {

[key] string ProductName;

// other fields ...
};

class Category {

[key] string CategoryName;

string Products[];

// other fields
}
```

La `Category` classe définit une propriété qui est un tableau des noms des produits qui appartiennent à cette catégorie.

Pour associer deux entités, vous devez définir une classe avec l' `Association` attribut dans le fichier MOF du schéma de ressource pour le service. La classe doit définir les deux entités à associer, appelées `ends` par l’Association. L’exemple suivant montre une définition d’une classe qui définit une association entre les entités Category et Products.

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

Vous devez également modifier la déclaration de la propriété Products dans la classe Category. Vous utilisez le `AssociationClass` mot clé pour spécifier que la propriété est une terminaison de l’Association. La propriété doit également être définie en tant que référence à une entité distincte, plutôt qu’en tant que tableau de chaînes. Pour ce faire, utilisez le `ref` mot clé. L’exemple suivant illustre la définition de propriété pour l’Association.

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

Enfin, vous devez déclarer l’autre terminaison de l’Association en ajoutant une définition de propriété à la `Product` classe. Il s’agit d’une référence à un tableau ou à une entité unique. En supposant que chaque produit appartient à une seule catégorie, la définition serait la suivante.

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

Les propriétés qui représentent les deux terminaisons de l’Association sont appelées propriétés de navigation.

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a>Étapes pour associer des entités dans le fichier de schéma de ressource

- Définissez l’Association en tant que classe à l’aide du `Association` mot clé.

- Définissez les terminaisons de l’Association en utilisant le mot clé AssociationClass pour qualifier les propriétés des entités associées.

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a>Création de l’Association dans le fichier XML de mappage des ressources

Il existe trois cas différents à prendre en compte lors du mappage d’une association dans le fichier XML de mappage des ressources.

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a>Détermination de la manière d’associer des entités dans le fichier de mappage des ressources

- Si la propriété de navigation est présente dans le sous-jacent. .NET Framework type, et cette propriété contient des clés étrangères, aucun mappage explicite n’est nécessaire.

- Si la propriété de navigation n’existe pas dans le type de .NET Framework sous-jacent, vous devez spécifier une applet de commande qui récupère la liste des clés des instances associées. Pour ce faire, ajoutez un `Association` élément imbriqué sous l' `CmdletImplementation` élément, en suivant les éléments qui définissent le `cmdlets` pour les autres commandes CRUD.

  ```xml
  Class Name=" Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
                 <Cmdlet>Get-ProductsInCategory</Cmdlet>
                 <ParameterForThisObject>Category</ParameterForThisObject>
              </GetReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

- Si la propriété de navigation existe dans le type de .NET Framework sous-jacent, mais qu’elle contient des instances d’objet au lieu de clés étrangères, vous devez créer une applet de commande (en écrivant une fonction ou un script Windows PowerShell) pour récupérer les clés étrangères. Vous spécifiez ensuite cette applet de commande dans le fichier de mappage des ressources. Par exemple, le script permettant de récupérer les clés devrait ressembler à ce qui suit.

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  Et le code XML du fichier de mappage des ressources ressemble à ce qui suit.

  ```xml
  Class Name=" Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
                 <Cmdlet>Get-ProductsInCategory.ps1</Cmdlet>
                 <ParameterForThisObject>Category</ParameterForThisObject>
              </GetReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

- En plus de spécifier une applet de commande pour récupérer les entités associées, vous pouvez également spécifier des applets de commande pour ajouter et supprimer des références de la collection. L’exemple suivant suppose que les applets de commande Add-ProductToCategory et Remove-ProductFromCategory existent (elles peuvent également être définies dans un script ou une fonction comme dans l’exemple précédent).

  ```xml
  Class Name="Sample.Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
  ...
              </GetReference>
        <AddReference>
     <CmdletName>"Add-ProductToCategory"</>
     <ParameterForThisObject>"Product"</>
     <ParameterForReferredObject>"Category"</>
        </AddReference>
        <RemoveReference>
     <CmdletName="Remove-ProductFromCategory"/>
     <ParameterForThisObject >"Product"</>
     <ParameterForReferredObject >"Category"</>
        </RemoveReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

## <a name="querying-associated-entities"></a>Interrogation des entités associées

Le client peut récupérer une liste des instances associées à une entité en créant des requêtes spécifiques.

#### <a name="constructing-queries-for-associated-entities"></a>Construction de requêtes pour les entités associées

- Un client peut demander les détails d’une catégorie sans récupérer ses produits associés. Par exemple, la requête suivante obtient les détails de la `food` catégorie.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  Pour obtenir les produits associés de la catégorie (mais pas les détails de la catégorie elle-même, le client spécifie la propriété de navigation dans la demande.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- Pour récupérer uniquement les URL des produits, utilisez le `$links` qualificateur dans la demande.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- Le client peut récupérer les détails de catégorie et les produits associés à l’aide du `$expand` qualificateur.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a>Voir aussi

[Création d’un service Web d’extension IIS de gestion OData](./creating-a-management-odata-web-service.md)
