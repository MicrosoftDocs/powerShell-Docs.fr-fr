---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,installation
title: Présentation du rôle de DSC dans un pipeline CI/CD
ms.openlocfilehash: 79740225c030974546035b67e0f873fa00aa690a
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279351"
---
# <a name="understanding-dscs-role-in-a-cicd-pipeline"></a>Présentation du rôle de DSC dans un pipeline CI/CD

Cet article décrit les différents types d’approches disponibles pour combiner des configurations et des ressources.
Dans chaque scénario, l’objectif est le même : réduire la complexité quand plusieurs configurations préférées existent pour parvenir à un état de fin de déploiement de serveur. Pour illustrer cela, citons par exemple un déploiement de serveur auquel participent plusieurs équipes, avec un propriétaire d’application qui gère l’état de l’application et une équipe centrale chargée de publier les modifications apportées aux bases de référence de sécurité. Les nuances de chaque approche, notamment les avantages et les risques qui leur sont associés, sont détaillés ici.

![Pipeline](media/authoringAdvanced/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a>Types de techniques de création collaborative

Deux solutions intégrées au gestionnaire de configuration local permettent de mettre en œuvre ce concept :

|        Concept         |                    Informations détaillées                     |
| ---------------------- | ----------------------------------------------------------- |
| Configurations partielles | [Documentation](../pull-server/partialConfigs.md)           |
| Ressources composites    | [Documentation](../resources/authoringResourceComposite.md) |

## <a name="understanding-the-impact-of-each-approach"></a>Comprendre l’impact de chaque approche

Chacune de ces solutions permet de gérer l’issue d’un déploiement de serveur. Cependant, chaque approche a un impact très différent.

## <a name="partial-configurations"></a>Configurations partielles

Quand vous utilisez des configurations partielles, le gestionnaire de configuration local est configuré pour gérer plusieurs configurations de manière indépendante. Les configurations sont compilées de manière indépendante avant d’être affectées au nœud. Le gestionnaire de configuration local doit pour cela être configuré à l’avance avec le nom de chaque configuration.

![PartialConfiguration](media/authoringAdvanced/PartialConfiguration.jpg)

Les configurations partielles permettent à deux équipes ou plus de contrôler entièrement la configuration d’un serveur, souvent sans l’avantage de la communication ou de la collaboration.

Des clients nous ont affirmé que cela pouvait occasionner des conflits de ressources, des remplacements involontaires et en fin de compte une véritable perte de contrôle de la configuration de la ressource.

De plus, en utilisant ce modèle, les modifications de configuration des équipes de contrôle ont peu de chances d’être entièrement testées via un pipeline de mise en production, ce qui conduit à des résultats inattendus en production.

**Il est très important d’utiliser un seul pipeline pour évaluer si toutes les modifications sont publiées sur les serveurs.**

Dans l’illustration ci-dessous, l’équipe B transmet sa configuration partielle à l’équipe A. L’équipe A exécute alors ses tests sur un serveur en appliquant les deux configurations. Dans ce modèle, une seule autorité est autorisée à apporter des modifications en production.

![PartialSinglePipeline](media/authoringAdvanced/PartialSinglePipeline.jpg)

Quand l’équipe B réclame des modifications, elle doit envoyer une demande de tirage (pull request) à l’environnement de contrôle de code source de l’équipe A. L’équipe A examine alors les modifications à l’aide de l’automation de test et les met en production dès qu’elle a l’assurance que les modifications n’entraîneront pas d’erreurs dans les applications ou les services hébergés par le serveur.

## <a name="composite-resources"></a>Ressources composites

Une ressource composite consiste simplement en une configuration DSC empaquetée comme ressource. Il n’existe aucune exigence de configuration particulière pour faire accepter les ressources composites au gestionnaire de configuration local. Celle-ci sont utilisées dans une nouvelle configuration et chaque compilation génère un fichier MOF.

![CompositeResource](media/authoringAdvanced/CompositeResource.jpg)

Il existe deux scénarios courants pour les ressources composites. Le premier vise à réduire la complexité et les concepts uniques et abstraits. Le deuxième vise à permettre l’empaquetage des bases de référence pour que l’équipe d’une application puisse la déployer en toute sécurité via son pipeline de mise en production une fois que tous les tests ont réussi.

```PowerShell
Configuration Name
{
  File 1
  {
    Ensure = "Present"
    Path = "c:\inetpub\file1.zip"
    Source = "http://uri/file1.zip"
  }
  Service A
  {
    Ensure = "Present"
    Name = "ServiceA"
    Status = "Running"
  }
  SecurityBaseline Settings
  {
    Ensure = "Present"
    Datacenter = "NorthAmerica"
  }
}
```

Les ressources composites facilitent la composition et la collaboration au moyen d’un pipeline tout en développant la maturité opérationnelle.

Vous utilisez peut-être déjà des ressources composites sans le savoir. **ServiceSet** en est un exemple.
Cette ressource gère l’état de plusieurs services Windows sans les mentionner individuellement. La propriété Name accepte un tableau de chaînes pour fournir le nom de chaque service. Une fois la configuration compilée, le fichier MOF contient une section Service pour chaque nom communiqué à ServiceSet.

Les organisations peuvent avoir des « agents » ou des « intergiciels (middleware) » à installer sur chaque serveur. Une ressource composite est la meilleure réponse pour gérer les dépendances, l’installation et la configuration de ces outils et utilitaires.

La personne ou l’équipe en charge des solutions qui englobent plusieurs serveurs crée une configuration qui intègre leurs exigences. Ensuite, la configuration est empaquetée sous forme de ressource composite selon les instructions fournies dans la documentation sur les ressources composites. Enfin, la nouvelle ressource composite doit être publiée à un emplacement, par exemple dans un partage de fichiers ou un flux NuGet, d’où elle peut être utilisée dans les configurations des équipes de l’application.

Chaque fois qu’une équipe publie une nouvelle version, elle incrémente le numéro de version dans le manifeste de module de leur ressource composite. Les équipes de l’application incluent la ressource composite dans la configuration qu’elles créent pour gérer les dépendances de l’application. Quand les équipes en charge des opérations et/ou de la sécurité publient une nouvelle version de leur ressource, elles adressent une notification aux équipes de l’application pour les informer de la nouvelle modification.

Les équipes de l’application peuvent déclencher une mise en production si la modification porte uniquement sur les bases de référence.
Cependant, cela donne l’occasion d’évaluer l’impact sur l’application avant de risquer une interruption de service.

> [!NOTE]
> L’utilisation des ressources composites a fait l’objet de commentaires critiques eu égard à la nécessité de compiler et de publier un nouveau fichier MOF à la suite de modifications. C'est la procédure normale. Chaque publication d’une nouvelle version doit inclure une référence statique à une version spécifique de chaque ressource et doit être validée par des tests avant d’être transmise aux nœuds du serveur de production. Le processus de test et de publication des modifications à partir du contrôle de code source crée un environnement sécurisé pour publier les modifications par lots de petite taille mais fréquents.

Pour plus d’informations sur l’utilisation des pipelines de mise en production pour gérer l’infrastructure de base, consultez le livre blanc : [The Release Pipeline Model](../further-reading/whitepapers.md).
