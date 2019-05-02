---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Résolution des problèmes des applets de commande
ms.openlocfilehash: f5cd9c0cc23fef5891bf02c10b6541ab0f9d418a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084179"
---
# <a name="troubleshooting-cmdlets"></a>Résolution des problèmes des applets de commande

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Comment résoudre le problème « Avertissement : Échec du téléchargement du package 'nom_de_votre_package' »

Il a été signalé que `Install-Module` ou `Update-Module` échouait parfois sur certains ordinateurs.
Selon nos recherches, cela est en rapport avec la connexion réseau.
Nous avons récemment mis à jour le fournisseur NuGet afin qu’il puisse télécharger des packages de façon fiable.
Vous pouvez suivre les instructions ci-dessous pour installer la build la plus récente du fournisseur NuGet, puis installer ou mettre à jour votre module.
Utilisons le module « Azure » à titre d’exemple ci-dessous.

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```
