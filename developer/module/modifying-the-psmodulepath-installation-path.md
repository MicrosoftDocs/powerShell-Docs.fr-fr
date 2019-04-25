---
title: Modifier le chemin d’Installation de PSModulePath | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082207"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>Modification du chemin d’Installation de PSModulePath

Le `PSModulePath` variable d’environnement stocke les chemins d’accès aux emplacements des modules qui sont installés sur le disque. Windows PowerShell utilise cette variable pour rechercher des modules lorsque l’utilisateur ne spécifie pas le chemin d’accès complet à un module. Les chemins d’accès dans cette variable sont recherchés dans l’ordre dans lequel ils apparaissent.

Lorsque Windows PowerShell démarre, `PSModulePath` est créé en tant que variable d’environnement système avec la valeur par défaut suivante : `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.

## <a name="to-view-the-psmodulepath-variable"></a>Pour afficher la variable PSModulePath

Pour afficher les chemins d’accès qui sont spécifiés dans le `PSModulePath` variable, tapez la commande suivante :

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>Pour ajouter des emplacements à la variable PSModulePath

Pour ajouter des chemins d’accès à cette variable, utilisez une des méthodes suivantes :

- Pour ajouter une valeur temporaire qui est disponible uniquement pour la session active, exécutez la commande suivante à la ligne de commande :

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- Pour ajouter une valeur persistante est disponible chaque fois qu’une session est ouverte, ajoutez la commande suivante pour un profil Windows PowerShell :

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  Pour plus d’informations sur les profils, consultez [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) dans la bibliothèque Microsoft TechNet.

- Pour ajouter une variable persistante dans le Registre, créez une nouvelle variable d’environnement utilisateur appelée `PSModulePath` à l’aide de l’éditeur de Variables d’environnement dans le **propriétés système** boîte de dialogue.

- Pour ajouter une variable persistante à l’aide d’un script, utilisez la **SetEnvironmentVariable** méthode sur la classe de l’environnement. Par exemple, le script suivant ajoute le « C:\Program Files\Fabrikam\Module chemin d’accès à la valeur de la variable d’environnement PSModulePath pour l’ordinateur. Pour ajouter le chemin d’accès à la variable d’environnement PSModulePath utilisateur, définissez la cible sur « Utilisateur ».

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>Pour supprimer des emplacements de PSModulePath

Vous pouvez supprimer des chemins d’accès de la variable à l’aide de méthodes similaires : par exemple, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` supprimera le **c:\ModulePath** chemin d’accès de la session active.

## <a name="see-also"></a>Voir aussi

[Écrire un Module PowerShell de Windows](./writing-a-windows-powershell-module.md)
