---
title: Modification du chemin d’installation de PSModulePath | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360668"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>Modification du chemin d’Installation de PSModulePath

La variable d’environnement `PSModulePath` stocke les chemins d’accès aux emplacements des modules installés sur le disque. Windows PowerShell utilise cette variable pour localiser les modules lorsque l’utilisateur ne spécifie pas le chemin d’accès complet à un module. Les chemins d’accès de cette variable sont recherchés dans l’ordre dans lequel ils apparaissent.

Au démarrage de Windows PowerShell, `PSModulePath` est créé en tant que variable d’environnement système avec la valeur par défaut suivante : `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.

## <a name="to-view-the-psmodulepath-variable"></a>Pour afficher la variable PSModulePath

Pour afficher les chemins d’accès spécifiés dans la variable `PSModulePath`, tapez la commande suivante :

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>Pour ajouter des emplacements à la variable PSModulePath

Pour ajouter des chemins d’accès à cette variable, utilisez l’une des méthodes suivantes :

- Pour ajouter une valeur temporaire qui est uniquement disponible pour la session active, exécutez la commande suivante sur la ligne de commande :

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- Pour ajouter une valeur persistante qui est disponible chaque fois qu’une session est ouverte, ajoutez la commande suivante à un profil Windows PowerShell :

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  Pour plus d’informations sur les profils, consultez [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) dans la bibliothèque Microsoft TechNet.

- Pour ajouter une variable persistante au registre, créez une nouvelle variable d’environnement utilisateur appelée `PSModulePath` à l’aide de l’éditeur de variables d’environnement dans la boîte de dialogue **Propriétés système** .

- Pour ajouter une variable persistante à l’aide d’un script, utilisez la méthode **SetEnvironmentVariable ne contient** sur la classe d’environnement. Par exemple, le script suivant ajoute le chemin d’accès C:\Program Files\Fabrikam\Module à la valeur de la variable d’environnement PSModulePath pour l’ordinateur. Pour ajouter le chemin d’accès à la variable d’environnement User PSModulePath, définissez la cible sur « User ».

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>Pour supprimer des emplacements du PSModulePath

Vous pouvez supprimer les chemins d’accès de la variable à l’aide de méthodes similaires : par exemple, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` supprime le chemin **c:\ModulePath** de la session active.

## <a name="see-also"></a>Voir aussi

[Écriture d’un module Windows PowerShell](./writing-a-windows-powershell-module.md)
