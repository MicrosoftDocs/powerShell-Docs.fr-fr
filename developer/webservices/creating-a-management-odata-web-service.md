---
title: Création d’un Service Web OData de gestion | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06b1b050-0bf7-48f5-ba05-43f489d597c0
caps.latest.revision: 10
ms.openlocfilehash: 476fce9fc087b870bad93a9204a820c5a84df99e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080694"
---
# <a name="creating-a-management-odata-web-service"></a><span data-ttu-id="494e5-102">Création d’un service web Management OData</span><span class="sxs-lookup"><span data-stu-id="494e5-102">Creating a Management OData Web Service</span></span>

<span data-ttu-id="494e5-103">Extension IIS Management ODATA est une infrastructure pour la création d’un point de terminaison ASP.NET web service qui expose vos données de gestion, accédées via les applets de commande Windows PowerShell et les scripts, en tant qu’entités de service OData Web.</span><span class="sxs-lookup"><span data-stu-id="494e5-103">Management ODATA IIS Extension is an infrastructure for creating an ASP.NET web service end point that exposes your management data, accessed through Windows PowerShell cmdlets and scripts, as OData Web service entities.</span></span> <span data-ttu-id="494e5-104">Elle fait en traitement des demandes d’OData et en les convertissant en un appel de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="494e5-104">It does that by processing OData requests and converting them into a Windows PowerShell invocation.</span></span> <span data-ttu-id="494e5-105">Les équipes produit peuvent se construire sur cette infrastructure pour créer des points de terminaison qui exposent des ensembles spécifiques de données de gestion.</span><span class="sxs-lookup"><span data-stu-id="494e5-105">Product teams can build on top of this infrastructure to create endpoints that expose specific sets of management data.</span></span>

<span data-ttu-id="494e5-106">Téléchargez et installez le [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) exemple.</span><span class="sxs-lookup"><span data-stu-id="494e5-106">Download and install the [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) sample.</span></span> <span data-ttu-id="494e5-107">Suivez les instructions pour déployer le service web.</span><span class="sxs-lookup"><span data-stu-id="494e5-107">Follow the instructions to deploy the web service.</span></span> <span data-ttu-id="494e5-108">Ce service web expose les Services et les processus via des opérations de création, lecture, mise à jour et suppression (CRUD).</span><span class="sxs-lookup"><span data-stu-id="494e5-108">This web service exposes Services and Processes through Create, Read, Update, and Delete (CRUD) operations.</span></span> <span data-ttu-id="494e5-109">Demandes CRUD effectuées au service web appellent des commandes Windows PowerShell qui effectuent les opérations demandées.</span><span class="sxs-lookup"><span data-stu-id="494e5-109">CRUD requests made to the web service invoke  Windows PowerShell commands that perform the requested operations.</span></span> <span data-ttu-id="494e5-110">Un mappage entre les opérations CRUD et les commandes Windows PowerShell sous-jacente est implémenté par le fichier schema.xml, Schema.MOF et fichiers de schéma deux.</span><span class="sxs-lookup"><span data-stu-id="494e5-110">A mapping between the CRUD operations and the underlying Windows PowerShell commands is implemented by two schema files, schema.mof and schema.xml.</span></span> <span data-ttu-id="494e5-111">Le fichier Schema.MOF utilise le [Distributed Management Task Force](https://www.dmtf.org/) standard de (DMTF) MOF (Managed Object).</span><span class="sxs-lookup"><span data-stu-id="494e5-111">The schema.mof file uses the [Distributed Management  Task Force](https://www.dmtf.org/) (DMTF) Managed Object (MOF) standard.</span></span> <span data-ttu-id="494e5-112">Le fichier schema.xml utilise un schéma XML qui est décrit dans [schéma de mappage de la ressource](./resource-mapping-schema.md).</span><span class="sxs-lookup"><span data-stu-id="494e5-112">The schema.xml file uses an XML schema that is described in [Resource Mapping Schema](./resource-mapping-schema.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="494e5-113">Avant d’activer les Extension IIS Management ODATA sur Windows Server 2008 R2 SP1, les fonctionnalités suivantes doivent être activées.</span><span class="sxs-lookup"><span data-stu-id="494e5-113">Before you enabling Management ODATA IIS Extension on Windows Server 2008 R2 SP1, the following features must be enabled.</span></span>
>
> 1.  <span data-ttu-id="494e5-114">IIS-WebServerRole</span><span class="sxs-lookup"><span data-stu-id="494e5-114">IIS-WebServerRole</span></span>
> 2.  <span data-ttu-id="494e5-115">IIS-WebServer</span><span class="sxs-lookup"><span data-stu-id="494e5-115">IIS-WebServer</span></span>
> 3.  <span data-ttu-id="494e5-116">IIS-HttpTracing</span><span class="sxs-lookup"><span data-stu-id="494e5-116">IIS-HttpTracing</span></span>
> 4.  <span data-ttu-id="494e5-117">IIS-ManagementOData</span><span class="sxs-lookup"><span data-stu-id="494e5-117">IIS-ManagementOData</span></span>

## <a name="steps-for-creating-a-management-odata-web-service"></a><span data-ttu-id="494e5-118">Étapes de création d’un service web de gestion OData</span><span class="sxs-lookup"><span data-stu-id="494e5-118">Steps for creating a Management OData web service</span></span>

<span data-ttu-id="494e5-119">Les rubriques suivantes décrivent comment créer et déployer un service web de gestion OData.</span><span class="sxs-lookup"><span data-stu-id="494e5-119">The following topics describe how to create and deploy a Management OData web service.</span></span>

- [<span data-ttu-id="494e5-120">Ajout de ressources à un Service Web OData de gestion</span><span class="sxs-lookup"><span data-stu-id="494e5-120">Adding Resources to a Management OData Web Service</span></span>](./adding-resources-to-a-management-odata-web-service.md)

- [<span data-ttu-id="494e5-121">Implémentation d’une autorisation personnalisée pour un service web de gestion OData</span><span class="sxs-lookup"><span data-stu-id="494e5-121">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [<span data-ttu-id="494e5-122">Mise en œuvre Configurationsession pour un service web de gestion OData</span><span class="sxs-lookup"><span data-stu-id="494e5-122">Implementing SessionConfiguration for a Management OData web service</span></span>](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [<span data-ttu-id="494e5-123">Le fichier de schéma MOF pour un service web de gestion OData</span><span class="sxs-lookup"><span data-stu-id="494e5-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="494e5-124">Le fichier de schéma XML pour un service web de gestion OData</span><span class="sxs-lookup"><span data-stu-id="494e5-124">Authoring the XML schema file for a Management OData web service</span></span>](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="494e5-125">Le fichier Web.config pour un service web de gestion OData</span><span class="sxs-lookup"><span data-stu-id="494e5-125">Authoring the Web.config file for a Management OData web service</span></span>](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="494e5-126">Déploiement d’un service web de gestion OData</span><span class="sxs-lookup"><span data-stu-id="494e5-126">Deploying a Management OData web service</span></span>](./deploying-a-management-odata-web-service.md)

- [<span data-ttu-id="494e5-127">Association d’entités de gestion OData</span><span class="sxs-lookup"><span data-stu-id="494e5-127">Associating Management OData Entities</span></span>](./associating-management-odata-entities.md)

## <a name="see-also"></a><span data-ttu-id="494e5-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="494e5-128">See Also</span></span>

[<span data-ttu-id="494e5-129">Fichiers de schéma d’Extension de gestion IIS d’ODATA</span><span class="sxs-lookup"><span data-stu-id="494e5-129">Management ODATA IIS Extension Schema Files</span></span>](./management-odata-iis-extension-schema-files.md)
