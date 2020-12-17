---
ms.date: 12/01/2020
title: Résolution des problèmes des applets de commande
description: Cet article fournit des informations et les étapes pour résoudre les erreurs à l’aide de PowerShell Gallery
ms.openlocfilehash: 980da8ea7b8a09513f33a9939d512c437b755d8d
ms.sourcegitcommit: 560a9f3c3148acab4655e91e8b07745ab74d5d26
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913316"
---
# <a name="troubleshooting-cmdlets"></a>Résolution des problèmes des applets de commande

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Comment résoudre le problème « Avertissement : Échec du téléchargement du package 'nom_de_votre_package' »

Il a été signalé que `Install-Module` ou `Update-Module` échouait parfois sur certains ordinateurs. Selon nos recherches, cela est en rapport avec la connexion réseau. Nous avons récemment mis à jour le fournisseur NuGet afin qu’il puisse télécharger des packages de façon fiable. Vous pouvez suivre les instructions ci-dessous pour installer la build la plus récente du fournisseur NuGet, puis installer ou mettre à jour votre module. Utilisons le module « Azure » à titre d’exemple ci-dessous.

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

## <a name="required-network-endpoints"></a>Points de terminaison réseau requis

Les cmdlets d’installation et de mise à jour nécessitent un accès à Internet pour se connecter aux points de terminaison réseau utilisés par PowerShell Gallery. Assurez-vous que vos stratégies d’accès réseau vous permettent de vous connecter aux points de terminaison suivants.

- `psg-prod-eastus.azureedge.net` - nom d'hôte CDN
- `az818661.vo.msecnd.net` - nom d'hôte CDN
- `devopsgallerystorage.blob.core.windows.net` - nom d’hôte du compte de stockage
- `*.powershellgallery.com` - site web
- `go.microsoft.com` - service de redirection

> [!NOTE]
> Les applets de commande qui interagissent avec PowerShell Gallery peuvent échouer avec des erreurs inattendues en cas d’arrêt des services PowerShell Gallery. Pour afficher l’état actuel de PowerShell Gallery, consultez la page [État de PowerShell Gallery](https://github.com/PowerShell/PowerShellGallery/blob/master/psgallery_status.md) sur GitHub.
