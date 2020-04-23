---
title: Utilisation de PowerShell dans Docker
description: Guide pratique pour utiliser PowerShell préinstallé dans une image Docker.
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/03/2020
ms.openlocfilehash: b16a31a04ca863ab55c7c9718b1a1a973e61ee46
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "80646371"
---
# <a name="using-powershell-in-docker"></a>Utilisation de PowerShell dans Docker

Nous publions les images Docker avec PowerShell préinstallé. Cet article explique comment prendre en main PowerShell dans le conteneur Docker.

## <a name="finding-available-images"></a>Recherche d’images disponibles

La version 17.05 ou une version plus récente de Docker est nécessaire pour les images publiées. Il faut également être en mesure d’exécuter Docker sans `sudo` ni droits d’administrateur local. Suivez les [instructions][install] officielles de Docker pour installer `docker` correctement.

Les conteneurs de version dérivent de l’image de distribution officielle, par exemple `centos:7`, puis installent les dépendances et enfin le package PowerShell.

Ces conteneurs se trouvent à l’adresse [hub.docker.com/r/microsoft/powershell][docker-release].

Pour plus d’informations sur ces images Docker, consultez le référentiel [PowerShell-Docker][PowerShell-Docker] sur GitHub.

## <a name="using-powershell-in-a-container"></a>Utilisation de PowerShell dans un conteneur

Les étapes suivantes montrent les commandes Docker nécessaires pour télécharger l’image et lancer une session PowerShell interactive.

```console
docker run -it mcr.microsoft.com/powershell
```

### <a name="remove-the-image-when-no-longer-needed"></a>Suppression de l’image quand elle n’est plus nécessaire

La commande suivante permet de supprimer l’image Docker lorsqu’elle n’est plus nécessaire.

```console
docker rmi mcr.microsoft.com/powershell
```

## <a name="legal-and-licensing"></a>Licences et informations juridiques

PowerShell est concédé sous [licence MIT][].

### <a name="windows-docker-file-and-image-licenses"></a>Licences d’images et de fichiers Windows Docker

En demandant et en utilisant l’image de système d’exploitation des conteneurs Windows, vous reconnaissez, comprenez et acceptez les termes du contrat de licence supplémentaires disponibles sur Docker Hub :

- [Windows Server Core][Window Server Core]
- [Nano Server][Nano Server]

### <a name="telemetry"></a>Télémétrie

Par défaut, PowerShell collecte des données de télémétrie limitées sans informations d’identification personnelle pour faciliter le développement de ses futures versions. Pour refuser l’envoi de données de télémétrie, créez une variable d’environnement nommée `POWERSHELL_TELEMETRY_OPTOUT` et définie sur la valeur `1` avant de lancer PowerShell à partir de l’emplacement d’installation. Les données de télémétrie que nous collectons relèvent de la [Déclaration de confidentialité Microsoft][privacy].

<!-- link references -->
[install]: https://docs.docker.com/engine/installation/
[docker-release]: https://hub.docker.com/r/microsoft/powershell/
[appinsights]: https://azure.microsoft.com/services/application-insights/
[Licence MIT]: https://github.com/PowerShell/PowerShell/tree/master/LICENSE.txt
[PowerShell-Docker]: https://github.com/PowerShell/PowerShell-Docker
[Window Server Core]: https://hub.docker.com/r/microsoft/windowsservercore/
[Nano Server]: https://hub.docker.com/r/microsoft/nanoserver/
[privacy]: https://privacy.microsoft.com/privacystatement/
