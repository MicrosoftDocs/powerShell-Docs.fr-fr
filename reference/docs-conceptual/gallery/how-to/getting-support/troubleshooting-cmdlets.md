---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Résolution des problèmes des applets de commande
ms.openlocfilehash: d87c680472c2588efbfe8b3c4d6f2dbee6883a0c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352106"
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
- [www.powershellgallery.com](www.powershellgallery.com)
- devopsgallerystorage.blob.core.windows.net
