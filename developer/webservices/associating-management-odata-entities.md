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
ms.openlocfilehash: 44b718e024eb98ac562edb50076287a31f5edc6b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860825"
---
# <a name="associating-management-odata-entities"></a>Association d’entités Management OData

Il est souvent utile de créer une association entre deux entités de gestion OData différents. Par exemple, un service de gestion OData peut avoir des entités qui gèrent un catalogue de produits qui sont organisés en catégories et définir les entités `Product` et `Category`. En associant ces deux entités, un client peut obtenir des informations sur tous les produits dans une catégorie avec une seule demande au service web.

Vous pouvez télécharger un exemple qui montre comment créer des associations entre entités à [exemple d’Association](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).

## <a name="creating-the-association-in-the-resource-schema-file"></a>Création de l’Association dans le fichier de schéma de ressources

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

Le `Category` classe définit une propriété qui est un tableau des noms de produits qui appartiennent à cette catégorie.

Pour associer les deux entités, vous devez définir une classe avec le `Association` attribut du fichier de ressources schéma MOF pour le service. La classe doit définir les deux entités associées, appelé `ends` de l’association. L’exemple suivant montre une définition d’une classe qui définit une association entre les entités de catégorie et les produits.

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

Vous devez également modifier la déclaration de la propriété de produits dans la classe de catégorie. Vous utilisez le `AssociationClass` mot clé pour spécifier que la propriété est une extrémité de l’association. La propriété doit également être définie en tant que référence à une entité distincte, plutôt qu’un tableau de chaînes. Pour cela, vous devez utiliser le `ref` mot clé. L’exemple suivant montre la définition de propriété pour l’association.

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

Enfin, vous devez déclarer l’autre extrémité de l’association en ajoutant une définition de propriété pour la `Product` classe. Il s’agit d’une référence à un tableau ou à une seule entité. En supposant que chaque produit appartient à qu’une seule catégorie, la définition se présente comme suit.

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

Les propriétés qui représentent les deux extrémités de l’association sont appelées propriétés de navigation.

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a>Étapes permettant d’associer des entités dans le fichier de schéma de ressources

- Définir l’association en tant que classe à l’aide de la `Association` mot clé.

- Définissent les terminaisons de l’association à l’aide du mot clé ClasseAssociation pour qualifier les propriétés des entités associées.

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a>Création de l’association dans le fichier XML de mappage de ressource

Il existe trois cas différents à prendre en compte lors du mappage d’une association dans le fichier XML de mappage de ressource.

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a>Déterminer comment associer des entités dans le fichier de mappage des ressources

- Si la propriété de navigation est présente dans sous-jacent. Type .NET framework, et cette propriété contient les clés étrangères, aucun mappage explicite est nécessaire.

- Si la propriété de navigation n’existe pas dans le type sous-jacent de .NET Framework, vous devez spécifier une applet de commande qui Récupère la liste des clés des instances associées. Pour cela, ajoutez un `Association` élément imbriqué sous le `CmdletImplementation` élément, en suivant les éléments qui définissent le `cmdlets` pour les autres commandes CRUD.

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

- Si la propriété de navigation existe dans le type sous-jacent de .NET Framework, mais il contient des instances d’objet au lieu de clés étrangères, vous devez créer une applet de commande (par écrire une fonction de Windows PowerShell ou un script) pour récupérer les clés étrangères. Puis, vous spécifiez cette applet de commande dans le fichier de mappage des ressources. Par exemple, le script pour récupérer les clés se présenterait comme suit.

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  Et le code XML dans le fichier de mappage des ressources ressemblerait à ce qui suit.

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

- Outre la spécification d’une applet de commande pour récupérer les entités associées, vous pouvez également spécifier des applets de commande pour ajouter et supprimer des références à partir de la collection. L’exemple suivant suppose que les applets de commande Add-ProductToCategory et Remove-ProductFromCategory existent (ils peuvent être également définis dans un script ou une fonction, comme dans l’exemple précédent).

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

#### <a name="constructing-queries-for-associated-entities"></a>Création de requêtes pour les entités associées

- Un client peut demander les détails d’une catégorie sans récupérer ses produits associés. Par exemple, la requête suivante obtient les détails de la `food` catégorie.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  Pour obtenir les produits associés de la catégorie (mais pas les détails de la catégorie proprement dit, le client spécifie la propriété de navigation dans la demande.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- Pour récupérer uniquement les URL des produits, utilisez le `$links` qualificateur dans la demande.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- Le client peut obtenir les détails de catégorie et de ses produits associés à l’aide de la `$expand` qualificateur.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a>Voir aussi

[Création d’un Service Web de gestion OData IIS Extension](./creating-a-management-odata-web-service.md)