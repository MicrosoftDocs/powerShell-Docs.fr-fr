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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856625"
---
# <a name="creating-a-management-odata-web-service"></a>Création d’un service web Management OData

Extension IIS Management ODATA est une infrastructure pour la création d’un point de terminaison ASP.NET web service qui expose vos données de gestion, accédées via les applets de commande Windows PowerShell et les scripts, en tant qu’entités de service OData Web. Elle fait en traitement des demandes d’OData et en les convertissant en un appel de Windows PowerShell. Les équipes produit peuvent se construire sur cette infrastructure pour créer des points de terminaison qui exposent des ensembles spécifiques de données de gestion.

Téléchargez et installez le [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) exemple. Suivez les instructions pour déployer le service web. Ce service web expose les Services et les processus via des opérations de création, lecture, mise à jour et suppression (CRUD). Demandes CRUD effectuées au service web appellent des commandes Windows PowerShell qui effectuent les opérations demandées. Un mappage entre les opérations CRUD et les commandes Windows PowerShell sous-jacente est implémenté par le fichier schema.xml, Schema.MOF et fichiers de schéma deux. Le fichier Schema.MOF utilise le [Distributed Management Task Force](https://www.dmtf.org/) standard de (DMTF) MOF (Managed Object). Le fichier schema.xml utilise un schéma XML qui est décrit dans [schéma de mappage de la ressource](./resource-mapping-schema.md).

> [!IMPORTANT]
> Avant d’activer les Extension IIS Management ODATA sur Windows Server 2008 R2 SP1, les fonctionnalités suivantes doivent être activées.
>
> 1.  IIS-WebServerRole
> 2.  IIS-WebServer
> 3.  IIS-HttpTracing
> 4.  IIS-ManagementOData

## <a name="steps-for-creating-a-management-odata-web-service"></a>Étapes de création d’un service web de gestion OData

Les rubriques suivantes décrivent comment créer et déployer un service web de gestion OData.

- [Ajout de ressources à un Service Web OData de gestion](./adding-resources-to-a-management-odata-web-service.md)

- [Implémentation d’une autorisation personnalisée pour un service web de gestion OData](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [Mise en œuvre Configurationsession pour un service web de gestion OData](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [Le fichier de schéma MOF pour un service web de gestion OData](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [Le fichier de schéma XML pour un service web de gestion OData](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [Le fichier Web.config pour un service web de gestion OData](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [Déploiement d’un service web de gestion OData](./deploying-a-management-odata-web-service.md)

- [Association d’entités de gestion OData](./associating-management-odata-entities.md)

## <a name="see-also"></a>Voir aussi

[Fichiers de schéma d’Extension de gestion IIS d’ODATA](./management-odata-iis-extension-schema-files.md)
