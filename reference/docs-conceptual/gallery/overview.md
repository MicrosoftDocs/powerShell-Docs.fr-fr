---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery, powershell, applet de commande, psgallery, psget
title: PowerShell Gallery
ms.openlocfilehash: d3e3b9d8bb3d6cefd3a3bfe79b012bb1dc1d8a2d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71327860"
---
# <a name="the-powershell-gallery"></a>PowerShell Gallery

PowerShell Gallery est le référentiel central pour le contenu PowerShell. Vous pouvez y trouver des modules PowerShell utiles contenant les commandes PowerShell et les ressources DSC (Configuration de l’état souhaité).
Vous pouvez également trouver des scripts PowerShell, certains d’entre eux peuvent contenir des workflows PowerShell qui présentent une série de tâches et donnent le séquencement de ces tâches. Certains de ces packages sont créés par Microsoft, d’autres par la communauté PowerShell.

## <a name="powershellget-overview"></a>Vue d’ensemble de PowerShellGet

Le module PowerShellGet contient des applets de commande permettant de détecter, d’installer, de mettre à jour et de publier des packages PowerShell contenant des artefacts tels que les modules, les ressources DSC, les fonctionnalités de rôle et les scripts à partir du référentiel [PowerShell Gallery](https://www.PowerShellGallery.com) et d’autres référentiels privés.

## <a name="getting-started-with-the-gallery"></a>Prise en main de la galerie

L’installation de packages de la galerie nécessite la dernière version du module PowerShellGet.
Pour des instructions complètes, consultez [Installation de PowerShellGet](installing-psget.md).

Pour plus d’informations sur l’utilisation des commandes PowerShellGet avec la galerie, consultez la page [Getting Started](getting-started.md). Vous pouvez également exécuter *Update-Help-Module PowerShellGet* pour installer l’aide locale sur ces commandes.

## <a name="supported-operating-systems"></a>Systèmes d’exploitation pris en charge

Le module **PowerShellGet** exige **Windows PowerShell 3.0 ou une version plus récente**, ou **PowerShell Core 6.0 ou une version plus récente**.

Une version adaptée de **Windows PowerShell** est disponible pour ces systèmes d’exploitation :

- Windows 10
- Windows 8.1 Professionnel
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2019
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**PowerShellGet** nécessite .NET Framework 4.5 ou ultérieur. Vous pouvez installer .NET Framework 4.5 ou ultérieur à partir [d’ici](https://msdn.microsoft.com/library/5a4x27ek.aspx).

Dans la mesure où **PowerShell Core** est multiplateforme et qu’il fonctionne sous Windows, Linux et macOS, **PowerShellGet** est également disponible sur ces systèmes. Pour obtenir une liste complète des systèmes pris en charge par **PowerShell Core** consultez [Installation de PowerShell](/powershell/scripting/setup/installing-powershell).

De nombreux modules hébergés dans la galerie prendront en charge différents systèmes d’exploitation en imposant des exigences supplémentaires. Pour plus d’informations, voir la documentation des modules.

## <a name="got-a-question-have-feedback"></a>Vous avez une question ? Vous avez des commentaires ?

Des informations supplémentaires relatives à PowerShell Gallery et PowerShellGet sont disponibles dans la page [Getting Started](getting-started.md). Envoyez vos commentaires et signalez les problèmes à l’aide de [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).
