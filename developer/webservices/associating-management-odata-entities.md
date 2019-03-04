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
# <a name="associating-management-odata-entities"></a><span data-ttu-id="c088a-102">Association d’entités Management OData</span><span class="sxs-lookup"><span data-stu-id="c088a-102">Associating Management OData Entities</span></span>

<span data-ttu-id="c088a-103">Il est souvent utile de créer une association entre deux entités de gestion OData différents.</span><span class="sxs-lookup"><span data-stu-id="c088a-103">It is often useful to create an association between two different Management OData entities.</span></span> <span data-ttu-id="c088a-104">Par exemple, un service de gestion OData peut avoir des entités qui gèrent un catalogue de produits qui sont organisés en catégories et définir les entités `Product` et `Category`.</span><span class="sxs-lookup"><span data-stu-id="c088a-104">For example, a Management OData service could have entities that manage a catalogue of products that are organized in categories, and define the entities `Product` and `Category`.</span></span> <span data-ttu-id="c088a-105">En associant ces deux entités, un client peut obtenir des informations sur tous les produits dans une catégorie avec une seule demande au service web.</span><span class="sxs-lookup"><span data-stu-id="c088a-105">By associating these two entities, a client can get information about all of the products in a category with a single request to the web service.</span></span>

<span data-ttu-id="c088a-106">Vous pouvez télécharger un exemple qui montre comment créer des associations entre entités à [exemple d’Association](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).</span><span class="sxs-lookup"><span data-stu-id="c088a-106">A sample that shows how to create associations between entities can be downloaded at [Association sample](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).</span></span>

## <a name="creating-the-association-in-the-resource-schema-file"></a><span data-ttu-id="c088a-107">Création de l’Association dans le fichier de schéma de ressources</span><span class="sxs-lookup"><span data-stu-id="c088a-107">Creating the Association in the resource schema file</span></span>

<span data-ttu-id="c088a-108">Le fichier MOF suivant définit deux entités.</span><span class="sxs-lookup"><span data-stu-id="c088a-108">The following MOF defines two entities.</span></span> <span data-ttu-id="c088a-109">Nous allons créer une association entre eux.</span><span class="sxs-lookup"><span data-stu-id="c088a-109">We will create an association between them.</span></span>

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

<span data-ttu-id="c088a-110">Le `Category` classe définit une propriété qui est un tableau des noms de produits qui appartiennent à cette catégorie.</span><span class="sxs-lookup"><span data-stu-id="c088a-110">The `Category` class defines a property that is an array of the names of the products that belong to that category.</span></span>

<span data-ttu-id="c088a-111">Pour associer les deux entités, vous devez définir une classe avec le `Association` attribut du fichier de ressources schéma MOF pour le service.</span><span class="sxs-lookup"><span data-stu-id="c088a-111">To associate two entities, you must define a class with the `Association` attribute in the resource schema MOF file for the service.</span></span> <span data-ttu-id="c088a-112">La classe doit définir les deux entités associées, appelé `ends` de l’association.</span><span class="sxs-lookup"><span data-stu-id="c088a-112">The class must define the two entities to be associated, called `ends` of the association.</span></span> <span data-ttu-id="c088a-113">L’exemple suivant montre une définition d’une classe qui définit une association entre les entités de catégorie et les produits.</span><span class="sxs-lookup"><span data-stu-id="c088a-113">The following example shows a definition of a class that defines an association between the Category and Products entities.</span></span>

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

<span data-ttu-id="c088a-114">Vous devez également modifier la déclaration de la propriété de produits dans la classe de catégorie.</span><span class="sxs-lookup"><span data-stu-id="c088a-114">You must also change the declaration of the Products property in the Category class.</span></span> <span data-ttu-id="c088a-115">Vous utilisez le `AssociationClass` mot clé pour spécifier que la propriété est une extrémité de l’association.</span><span class="sxs-lookup"><span data-stu-id="c088a-115">You use the `AssociationClass` keyword to specify that the property is one end of the association.</span></span> <span data-ttu-id="c088a-116">La propriété doit également être définie en tant que référence à une entité distincte, plutôt qu’un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="c088a-116">The property must also be defined as a reference to a separate entity, rather than an array of strings.</span></span> <span data-ttu-id="c088a-117">Pour cela, vous devez utiliser le `ref` mot clé.</span><span class="sxs-lookup"><span data-stu-id="c088a-117">You do this by using the `ref` keyword.</span></span> <span data-ttu-id="c088a-118">L’exemple suivant montre la définition de propriété pour l’association.</span><span class="sxs-lookup"><span data-stu-id="c088a-118">The following example shows the property definition for the association.</span></span>

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

<span data-ttu-id="c088a-119">Enfin, vous devez déclarer l’autre extrémité de l’association en ajoutant une définition de propriété pour la `Product` classe.</span><span class="sxs-lookup"><span data-stu-id="c088a-119">Finally, you must declare the other end of the association by adding a property definition to the `Product` class.</span></span> <span data-ttu-id="c088a-120">Il s’agit d’une référence à un tableau ou à une seule entité.</span><span class="sxs-lookup"><span data-stu-id="c088a-120">This is a reference to either an array or to a single entity.</span></span> <span data-ttu-id="c088a-121">En supposant que chaque produit appartient à qu’une seule catégorie, la définition se présente comme suit.</span><span class="sxs-lookup"><span data-stu-id="c088a-121">Assuming that each product belongs to only one category, the definition would be as follows.</span></span>

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

<span data-ttu-id="c088a-122">Les propriétés qui représentent les deux extrémités de l’association sont appelées propriétés de navigation.</span><span class="sxs-lookup"><span data-stu-id="c088a-122">The properties that represent the two ends of the association are called navigation properties.</span></span>

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a><span data-ttu-id="c088a-123">Étapes permettant d’associer des entités dans le fichier de schéma de ressources</span><span class="sxs-lookup"><span data-stu-id="c088a-123">Steps for associating entities in the resource schema file</span></span>

- <span data-ttu-id="c088a-124">Définir l’association en tant que classe à l’aide de la `Association` mot clé.</span><span class="sxs-lookup"><span data-stu-id="c088a-124">Define the association as a class by using the `Association` keyword.</span></span>

- <span data-ttu-id="c088a-125">Définissent les terminaisons de l’association à l’aide du mot clé ClasseAssociation pour qualifier les propriétés des entités associées.</span><span class="sxs-lookup"><span data-stu-id="c088a-125">Define the ends of the association by using the AssociationClass keyword to qualify properties of the associated entities.</span></span>

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a><span data-ttu-id="c088a-126">Création de l’association dans le fichier XML de mappage de ressource</span><span class="sxs-lookup"><span data-stu-id="c088a-126">Creating the association in the resource mapping XML file</span></span>

<span data-ttu-id="c088a-127">Il existe trois cas différents à prendre en compte lors du mappage d’une association dans le fichier XML de mappage de ressource.</span><span class="sxs-lookup"><span data-stu-id="c088a-127">There are three different cases to consider when mapping an association in the resource mapping XML file.</span></span>

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a><span data-ttu-id="c088a-128">Déterminer comment associer des entités dans le fichier de mappage des ressources</span><span class="sxs-lookup"><span data-stu-id="c088a-128">Determining how to associate entities in the resource mapping file</span></span>

- <span data-ttu-id="c088a-129">Si la propriété de navigation est présente dans sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="c088a-129">If the navigation property is present in the underlying.</span></span> <span data-ttu-id="c088a-130">Type .NET framework, et cette propriété contient les clés étrangères, aucun mappage explicite est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="c088a-130">.NET Framework type, and that property contains foreign keys, no explicit mapping is necessary.</span></span>

- <span data-ttu-id="c088a-131">Si la propriété de navigation n’existe pas dans le type sous-jacent de .NET Framework, vous devez spécifier une applet de commande qui Récupère la liste des clés des instances associées.</span><span class="sxs-lookup"><span data-stu-id="c088a-131">If the navigation property does not exist in the underlying .NET Framework type, you must specify a cmdlet that retrieves the list of keys of the associated instances.</span></span> <span data-ttu-id="c088a-132">Pour cela, ajoutez un `Association` élément imbriqué sous le `CmdletImplementation` élément, en suivant les éléments qui définissent le `cmdlets` pour les autres commandes CRUD.</span><span class="sxs-lookup"><span data-stu-id="c088a-132">You do this by adding an `Association` element nested under the `CmdletImplementation` element, following the elements that define the `cmdlets` for the other CRUD commands.</span></span>

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

- <span data-ttu-id="c088a-133">Si la propriété de navigation existe dans le type sous-jacent de .NET Framework, mais il contient des instances d’objet au lieu de clés étrangères, vous devez créer une applet de commande (par écrire une fonction de Windows PowerShell ou un script) pour récupérer les clés étrangères.</span><span class="sxs-lookup"><span data-stu-id="c088a-133">If the navigation property does exist in the underlying .NET Framework type, but it contains object instances instead of foreign keys, then you must create a cmdlet (by writing a Windows PowerShell function or script) to retrieve the foreign keys.</span></span> <span data-ttu-id="c088a-134">Puis, vous spécifiez cette applet de commande dans le fichier de mappage des ressources.</span><span class="sxs-lookup"><span data-stu-id="c088a-134">You then specify that cmdlet in the resource mapping file.</span></span> <span data-ttu-id="c088a-135">Par exemple, le script pour récupérer les clés se présenterait comme suit.</span><span class="sxs-lookup"><span data-stu-id="c088a-135">For example, the script to retrieve the keys would look like the following.</span></span>

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  <span data-ttu-id="c088a-136">Et le code XML dans le fichier de mappage des ressources ressemblerait à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="c088a-136">And the XML in the resource mapping file would look like the following.</span></span>

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

- <span data-ttu-id="c088a-137">Outre la spécification d’une applet de commande pour récupérer les entités associées, vous pouvez également spécifier des applets de commande pour ajouter et supprimer des références à partir de la collection.</span><span class="sxs-lookup"><span data-stu-id="c088a-137">In addition to specifying a cmdlet to retrieve the associated entities, you can also specify cmdlets to add and remove references from the collection.</span></span> <span data-ttu-id="c088a-138">L’exemple suivant suppose que les applets de commande Add-ProductToCategory et Remove-ProductFromCategory existent (ils peuvent être également définis dans un script ou une fonction, comme dans l’exemple précédent).</span><span class="sxs-lookup"><span data-stu-id="c088a-138">The following example assumes that the Add-ProductToCategory and Remove-ProductFromCategory cmdlets exist (they can also be defined in a script or function as in the previous example).</span></span>

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

## <a name="querying-associated-entities"></a><span data-ttu-id="c088a-139">Interrogation des entités associées</span><span class="sxs-lookup"><span data-stu-id="c088a-139">Querying associated entities</span></span>

<span data-ttu-id="c088a-140">Le client peut récupérer une liste des instances associées à une entité en créant des requêtes spécifiques.</span><span class="sxs-lookup"><span data-stu-id="c088a-140">The client can retrieve a list of the instances associated with an entity by creating specific queries.</span></span>

#### <a name="constructing-queries-for-associated-entities"></a><span data-ttu-id="c088a-141">Création de requêtes pour les entités associées</span><span class="sxs-lookup"><span data-stu-id="c088a-141">Constructing queries for associated entities</span></span>

- <span data-ttu-id="c088a-142">Un client peut demander les détails d’une catégorie sans récupérer ses produits associés.</span><span class="sxs-lookup"><span data-stu-id="c088a-142">A client can request the details of a category without retrieving its associated products.</span></span> <span data-ttu-id="c088a-143">Par exemple, la requête suivante obtient les détails de la `food` catégorie.</span><span class="sxs-lookup"><span data-stu-id="c088a-143">For example, the following request gets details of the `food` category.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  <span data-ttu-id="c088a-144">Pour obtenir les produits associés de la catégorie (mais pas les détails de la catégorie proprement dit, le client spécifie la propriété de navigation dans la demande.</span><span class="sxs-lookup"><span data-stu-id="c088a-144">To get the associated products of the category (but not details of the category itself, the client specifies the navigation property in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- <span data-ttu-id="c088a-145">Pour récupérer uniquement les URL des produits, utilisez le `$links` qualificateur dans la demande.</span><span class="sxs-lookup"><span data-stu-id="c088a-145">To retrieve only URLs of the products, use the `$links` qualifier in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- <span data-ttu-id="c088a-146">Le client peut obtenir les détails de catégorie et de ses produits associés à l’aide de la `$expand` qualificateur.</span><span class="sxs-lookup"><span data-stu-id="c088a-146">The client can get both the category details and its associated products by using the `$expand` qualifier.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a><span data-ttu-id="c088a-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c088a-147">See Also</span></span>

[<span data-ttu-id="c088a-148">Création d’un Service Web de gestion OData IIS Extension</span><span class="sxs-lookup"><span data-stu-id="c088a-148">Creating a Management OData IIS Extension Web Service</span></span>](./creating-a-management-odata-web-service.md)