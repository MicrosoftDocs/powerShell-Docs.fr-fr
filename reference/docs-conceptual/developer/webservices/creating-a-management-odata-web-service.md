---
title: Création d’un service Web OData de gestion | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06b1b050-0bf7-48f5-ba05-43f489d597c0
caps.latest.revision: 10
ms.openlocfilehash: 476fce9fc087b870bad93a9204a820c5a84df99e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359718"
---
# <a name="creating-a-management-odata-web-service"></a>Création d’un service web Management OData

L’extension IIS de gestion ODATA est une infrastructure permettant de créer un point de terminaison de service Web ASP.NET qui expose vos données de gestion, accessibles via des applets de commande et des scripts Windows PowerShell, en tant qu’entités de service Web OData. Pour ce faire, il traite les demandes OData et les convertit en appel Windows PowerShell. Les équipes produit peuvent créer des points de terminaison qui exposent des ensembles spécifiques de données de gestion.

Téléchargez et installez l’exemple [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) . Suivez les instructions pour déployer le service Web. Ce service Web expose les services et les processus via des opérations CRUD (Create, Read, Update et Delete). Les demandes CRUD adressées au service Web appellent des commandes Windows PowerShell qui effectuent les opérations demandées. Un mappage entre les opérations CRUD et les commandes Windows PowerShell sous-jacentes est implémenté par deux fichiers de schéma, Schema. mof et Schema. Xml. Le fichier Schema. mof utilise la norme MOF ( [Distributed Management Task Force](https://www.dmtf.org/) ). Le fichier Schema. xml utilise un schéma XML qui est décrit dans [schéma de mappage des ressources](./resource-mapping-schema.md).

> [!IMPORTANT]
> Avant d’activer l’extension IIS Management ODATA sur Windows Server 2008 R2 SP1, les fonctionnalités suivantes doivent être activées.
>
> 1.  IIS-WebServerRole
> 2.  IIS-WebServer
> 3.  IIS-HttpTracing
> 4.  IIS-ManagementOData

## <a name="steps-for-creating-a-management-odata-web-service"></a>Étapes de création d’un service Web OData de gestion

Les rubriques suivantes décrivent comment créer et déployer un service Web OData de gestion.

- [Ajout de ressources à un service Web OData de gestion](./adding-resources-to-a-management-odata-web-service.md)

- [Implémentation d’une autorisation personnalisée pour un service Web OData de gestion](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [Implémentation de Configurationsession pour un service Web OData de gestion](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [Création du fichier de schéma MOF pour un service Web OData de gestion](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [Création du fichier de schéma XML pour un service Web OData de gestion](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [Création du fichier Web. config pour un service Web OData de gestion](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [Déploiement d’un service Web OData de gestion](./deploying-a-management-odata-web-service.md)

- [Association d’entités de gestion OData](./associating-management-odata-entities.md)

## <a name="see-also"></a>Voir aussi

[Fichiers de schéma d’extension IIS de gestion ODATA](./management-odata-iis-extension-schema-files.md)
