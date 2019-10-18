---
title: Création du fichier de schéma XML pour un service Web OData de gestion | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e83c9d9-6d06-4247-94d9-e3bfd4013b11
caps.latest.revision: 4
ms.openlocfilehash: a806d012097d107b6cc35710b9a93f2b27dd1ace
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359798"
---
# <a name="authoring-the-xml-schema-file-for-a-management-odata-web-service"></a><span data-ttu-id="e72ad-102">Création du fichier de schéma XML pour un service web Management OData</span><span class="sxs-lookup"><span data-stu-id="e72ad-102">Authoring the XML schema file for a Management OData web service</span></span>

<span data-ttu-id="e72ad-103">Une fois que vous avez défini les ressources que votre service Web exposera (voir [création du fichier de schéma MOF pour un service Web de gestion OData](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), vous mappez ces ressources aux cmdlets Windows PowerShell sous-jacentes qui implémentent les opérations prises en charge pour chaque ressource en créant un fichier XML conforme au schéma de mappage des [ressources](./resource-mapping-schema.md).</span><span class="sxs-lookup"><span data-stu-id="e72ad-103">After you define the resources your web service will expose (see [Authoring the MOF schema file for a Management OData web service](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), you map those resources to the underlying Windows PowerShell cmdlets that implement the supported operations for each resource by creating an XML file that conforms to the [Resource Mapping Schema](./resource-mapping-schema.md).</span></span> <span data-ttu-id="e72ad-104">Le fichier XML spécifie également les URL utilisées par le client pour accéder aux ressources.</span><span class="sxs-lookup"><span data-stu-id="e72ad-104">The XML file also specifies the URLs that are used by the client to access the resources.</span></span>

## <a name="mappng-resources-to-urls"></a><span data-ttu-id="e72ad-105">Mappng ressources aux URL</span><span class="sxs-lookup"><span data-stu-id="e72ad-105">Mappng resources to URLs</span></span>

<span data-ttu-id="e72ad-106">La première partie du fichier XML mappe les ressources définies dans le fichier de schéma MOF aux URL utilisées pour y accéder.</span><span class="sxs-lookup"><span data-stu-id="e72ad-106">The first part of the XML file maps the resources defined in the MOF schema file to the URLs that are used to access them.</span></span> <span data-ttu-id="e72ad-107">L’exemple suivant montre ce mappage.</span><span class="sxs-lookup"><span data-stu-id="e72ad-107">The following example shows that mapping.</span></span>

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

## <a name="mapping-cmdlets-to-crud-operations"></a><span data-ttu-id="e72ad-108">Mappage des applets de commande aux opérations CRUD</span><span class="sxs-lookup"><span data-stu-id="e72ad-108">Mapping cmdlets to CRUD operations</span></span>

<span data-ttu-id="e72ad-109">Vous spécifiez ensuite les applets de commande qui correspondent aux opérations CRUD (création, lecture, mise à jour et suppression) prises en charge par les ressources.</span><span class="sxs-lookup"><span data-stu-id="e72ad-109">You then specify the cmdlets that correspond to the CRUD (create, read, update, and delete) operations that the resources support.</span></span> <span data-ttu-id="e72ad-110">Dans le schéma de [mappage des ressources](./resource-mapping-schema.md)OData de gestion, les opérations CRUD sont mappées comme suit.</span><span class="sxs-lookup"><span data-stu-id="e72ad-110">In the Management OData [Resource Mapping Schema](./resource-mapping-schema.md), the CRUD operations are mapped as follows.</span></span>

|<span data-ttu-id="e72ad-111">Commande CRUD</span><span class="sxs-lookup"><span data-stu-id="e72ad-111">CRUD command</span></span>|<span data-ttu-id="e72ad-112">Élément XML</span><span class="sxs-lookup"><span data-stu-id="e72ad-112">XML element</span></span>|
|------------------|-----------------|
|<span data-ttu-id="e72ad-113">Créer</span><span class="sxs-lookup"><span data-stu-id="e72ad-113">Create</span></span>|<span data-ttu-id="e72ad-114">Créer</span><span class="sxs-lookup"><span data-stu-id="e72ad-114">Create</span></span>|
|<span data-ttu-id="e72ad-115">Lecture</span><span class="sxs-lookup"><span data-stu-id="e72ad-115">Read</span></span>|<span data-ttu-id="e72ad-116">Requête</span><span class="sxs-lookup"><span data-stu-id="e72ad-116">Query</span></span>|
|<span data-ttu-id="e72ad-117">Mettre à jour/Mise à jour</span><span class="sxs-lookup"><span data-stu-id="e72ad-117">Update</span></span>|<span data-ttu-id="e72ad-118">Mettre à jour/Mise à jour</span><span class="sxs-lookup"><span data-stu-id="e72ad-118">Update</span></span>|
|<span data-ttu-id="e72ad-119">Supprimer</span><span class="sxs-lookup"><span data-stu-id="e72ad-119">Delete</span></span>|<span data-ttu-id="e72ad-120">Supprimer</span><span class="sxs-lookup"><span data-stu-id="e72ad-120">Delete</span></span>|

<span data-ttu-id="e72ad-121">L’exemple suivant montre les mappages pour les opérations de création, de lecture et de mise à jour sur la ressource `Service`.</span><span class="sxs-lookup"><span data-stu-id="e72ad-121">The following example shows the mappings for the Create, Read, and Update operations on the `Service` resource.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e72ad-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e72ad-122">See Also</span></span>

[<span data-ttu-id="e72ad-123">Création du fichier de schéma MOF pour un service Web OData de gestion</span><span class="sxs-lookup"><span data-stu-id="e72ad-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="e72ad-124">Schéma de mappage des ressources</span><span class="sxs-lookup"><span data-stu-id="e72ad-124">Resource Mapping Schema</span></span>](./resource-mapping-schema.md)

[<span data-ttu-id="e72ad-125">Création d’un service Web OData de gestion</span><span class="sxs-lookup"><span data-stu-id="e72ad-125">Creating a Management OData Web Service</span></span>](./creating-a-management-odata-web-service.md)