---
title: Le fichier de schéma XML pour un service web de gestion OData | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e83c9d9-6d06-4247-94d9-e3bfd4013b11
caps.latest.revision: 4
ms.openlocfilehash: a806d012097d107b6cc35710b9a93f2b27dd1ace
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857975"
---
# <a name="authoring-the-xml-schema-file-for-a-management-odata-web-service"></a><span data-ttu-id="fa805-102">Création du fichier de schéma XML pour un service web Management OData</span><span class="sxs-lookup"><span data-stu-id="fa805-102">Authoring the XML schema file for a Management OData web service</span></span>

<span data-ttu-id="fa805-103">Après avoir défini les ressources de votre service web va exposer (voir [le fichier de schéma MOF pour un service web de gestion OData](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), vous mappez ces ressources pour les applets de commande Windows PowerShell sous-jacente qui implémentent la prise en charge opérations pour chaque ressource en créant un fichier XML qui est conforme à la [schéma de mappage de la ressource](./resource-mapping-schema.md).</span><span class="sxs-lookup"><span data-stu-id="fa805-103">After you define the resources your web service will expose (see [Authoring the MOF schema file for a Management OData web service](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), you map those resources to the underlying Windows PowerShell cmdlets that implement the supported operations for each resource by creating an XML file that conforms to the [Resource Mapping Schema](./resource-mapping-schema.md).</span></span> <span data-ttu-id="fa805-104">Le fichier XML spécifie également les URL utilisées par le client pour accéder aux ressources.</span><span class="sxs-lookup"><span data-stu-id="fa805-104">The XML file also specifies the URLs that are used by the client to access the resources.</span></span>

## <a name="mappng-resources-to-urls"></a><span data-ttu-id="fa805-105">Ressources Mappng aux URL</span><span class="sxs-lookup"><span data-stu-id="fa805-105">Mappng resources to URLs</span></span>

<span data-ttu-id="fa805-106">La première partie du fichier XML mappe les ressources définies dans le fichier de schéma MOF aux URL qui sont utilisées pour y accéder.</span><span class="sxs-lookup"><span data-stu-id="fa805-106">The first part of the XML file maps the resources defined in the MOF schema file to the URLs that are used to access them.</span></span> <span data-ttu-id="fa805-107">L’exemple suivant montre ce mappage.</span><span class="sxs-lookup"><span data-stu-id="fa805-107">The following example shows that mapping.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<ResourceMetadata xmlns="http://schemas.microsoft.com/powershell-web-services/2010/09">
    <SchemaNamespace>PswsTest</SchemaNamespace>
    <ContainerName>PSWSEntityContainer</ContainerName>
    <Resources>
        <Resource>
            <RelativeUrl>Service</RelativeUrl>
            <Class>PswsTest_Service</Class>
        </Resource>
        <Resource>
            <RelativeUrl>Process</RelativeUrl>
            <Class>PswsTest_Process</Class>
        </Resource>
    </Resources>
```

## <a name="mapping-cmdlets-to-crud-operations"></a><span data-ttu-id="fa805-108">Mappage des applets de commande pour les opérations CRUD</span><span class="sxs-lookup"><span data-stu-id="fa805-108">Mapping cmdlets to CRUD operations</span></span>

<span data-ttu-id="fa805-109">Vous devez ensuite spécifier les applets de commande qui correspondent à la CRUD (créer, lire, mettre à jour et supprimer) les opérations qui prennent en charge par les ressources.</span><span class="sxs-lookup"><span data-stu-id="fa805-109">You then specify the cmdlets that correspond to the CRUD (create, read, update, and delete) operations that the resources support.</span></span> <span data-ttu-id="fa805-110">Dans la gestion OData [schéma de mappage de la ressource](./resource-mapping-schema.md), les opérations CRUD sont mappées comme suit.</span><span class="sxs-lookup"><span data-stu-id="fa805-110">In the Management OData [Resource Mapping Schema](./resource-mapping-schema.md), the CRUD operations are mapped as follows.</span></span>

|<span data-ttu-id="fa805-111">Commande CRUD</span><span class="sxs-lookup"><span data-stu-id="fa805-111">CRUD command</span></span>|<span data-ttu-id="fa805-112">Élément XML</span><span class="sxs-lookup"><span data-stu-id="fa805-112">XML element</span></span>|
|------------------|-----------------|
|<span data-ttu-id="fa805-113">Create</span><span class="sxs-lookup"><span data-stu-id="fa805-113">Create</span></span>|<span data-ttu-id="fa805-114">Create</span><span class="sxs-lookup"><span data-stu-id="fa805-114">Create</span></span>|
|<span data-ttu-id="fa805-115">Lecture</span><span class="sxs-lookup"><span data-stu-id="fa805-115">Read</span></span>|<span data-ttu-id="fa805-116">Requête</span><span class="sxs-lookup"><span data-stu-id="fa805-116">Query</span></span>|
|<span data-ttu-id="fa805-117">Mise à jour</span><span class="sxs-lookup"><span data-stu-id="fa805-117">Update</span></span>|<span data-ttu-id="fa805-118">Mise à jour</span><span class="sxs-lookup"><span data-stu-id="fa805-118">Update</span></span>|
|<span data-ttu-id="fa805-119">Supprimer</span><span class="sxs-lookup"><span data-stu-id="fa805-119">Delete</span></span>|<span data-ttu-id="fa805-120">Supprimer</span><span class="sxs-lookup"><span data-stu-id="fa805-120">Delete</span></span>|

<span data-ttu-id="fa805-121">L’exemple suivant montre les mappages pour les opérations de création, lecture et mise à jour sur le `Service` ressource.</span><span class="sxs-lookup"><span data-stu-id="fa805-121">The following example shows the mappings for the Create, Read, and Update operations on the `Service` resource.</span></span>

```xml
<ClassImplementations>
        <Class>
            <Name>PswsTest_Service</Name>
            <CmdletImplementation>
                <Query>
                    <Cmdlet>Get-Service</Cmdlet>
                        <FieldParameterMap>
                            <Field>
                                <FieldName>ServiceName</FieldName>
                                <ParameterName>Name</ParameterName>
                            </Field>
                        </FieldParameterMap>
                        <ParameterSets>
                            <ParameterSet>
                                <Name>Default</Name>
                                <Parameter><Name>Name</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                            </ParameterSet>
                            <ParameterSet>
                                <Name>DisplayName</Name>
                                <Parameter><Name>DisplayName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                            </ParameterSet>
                            <ParameterSet>
                                <Name>InputObject</Name>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Query>
                <Update>
                    <Cmdlet>Set-Service</Cmdlet>
                    <FieldParameterMap>
                        <Field>
                            <FieldName>ServiceName</FieldName>
                            <ParameterName>Name</ParameterName>
                        </Field>
                    </FieldParameterMap>
                    <ParameterSets>
                        <ParameterSet>
                            <Name>Name</Name>
                            <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                            <Parameter><Name>Name</Name></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                            <Parameter><Name>Status</Name></Parameter>
                            <Parameter><Name>ErrorVariable</Name></Parameter>
                            <Parameter><Name>WarningVariable</Name></Parameter>
                            <Parameter><Name>OutVariable</Name></Parameter>
                            <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                        <ParameterSet>
                            <Name>InputObject</Name>
                            <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Update>
                <Create>
                    <Cmdlet>New-Service</Cmdlet>
                    <FieldParameterMap>
                        <Field>
                            <FieldName>ServiceName</FieldName>
                            <ParameterName>Name</ParameterName>
                        </Field>
                    </FieldParameterMap>
                    <ParameterSets>
                        <ParameterSet>
                            <Name>__AllParameterSets</Name>
                            <Parameter><Name>BinaryPathName</Name></Parameter>
                            <Parameter><Name>Name</Name></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                            <Parameter><Name>DependsOn</Name></Parameter>
                            <Parameter><Name>ErrorVariable</Name></Parameter>
                            <Parameter><Name>WarningVariable</Name></Parameter>
                            <Parameter><Name>OutVariable</Name></Parameter>
                            <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Create>
            </CmdletImplementation>
        </Class>
```

## <a name="see-also"></a><span data-ttu-id="fa805-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa805-122">See Also</span></span>

[<span data-ttu-id="fa805-123">Le fichier de schéma MOF pour un service web de gestion OData</span><span class="sxs-lookup"><span data-stu-id="fa805-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="fa805-124">Schéma de mappage des ressources</span><span class="sxs-lookup"><span data-stu-id="fa805-124">Resource Mapping Schema</span></span>](./resource-mapping-schema.md)

[<span data-ttu-id="fa805-125">Création d’un Service Web OData de gestion</span><span class="sxs-lookup"><span data-stu-id="fa805-125">Creating a Management OData Web Service</span></span>](./creating-a-management-odata-web-service.md)