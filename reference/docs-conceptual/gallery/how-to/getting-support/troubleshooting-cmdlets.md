---
ms.date: 06/12/2017
title: Résolution des problèmes des applets de commande
description: Cet article fournit des informations et les étapes pour résoudre les erreurs à l’aide de PowerShell Gallery
ms.openlocfilehash: db9e58c185c6f3bca26ff3639af85fa2dba48909
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661058"
---
# <a name="troubleshooting-cmdlets"></a>Résolution des problèmes des applets de commande

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Comment résoudre le problème « Avertissement : Échec du téléchargement du package 'nom_de_votre_package' »

Il a été signalé que `Install-Module` ou `Update-Module` échouait parfois sur certains ordinateurs. Selon nos recherches, cela est en rapport avec la connexion réseau. Nous avons récemment mis à jour le fournisseur NuGet afin qu’il puisse télécharger des packages de façon fiable. Vous pouvez suivre les instructions ci-dessous pour installer la build la plus récente du fournisseur NuGet, puis installer ou mettre à jour votre module. Utilisons le module « Azure » à titre d’exemple ci-dessous.

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

### <a name="required-network-endpoints"></a>Points de terminaison réseau requis

Les cmdlets d’installation et de mise à jour nécessitent un accès à Internet pour se connecter aux points de terminaison réseau utilisés par PowerShell Gallery. Assurez-vous que vos stratégies d’accès réseau vous permettent de vous connecter aux points de terminaison suivants.

- oneget.org
- go.microsoft.com
- az818661.vo.msecnd.net
- www.powershellgallery.com
- devopsgallerystorage.blob.core.windows.net
