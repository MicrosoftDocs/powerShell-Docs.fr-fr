---
ms.date: 09/13/2016
ms.topic: reference
title: Modification du chemin d’Installation de PSModulePath
description: Modification du chemin d’Installation de PSModulePath
ms.openlocfilehash: b802492bf9b49e8165e296817e3f80b9ae8265a6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92661940"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>Modification du chemin d’Installation de PSModulePath

La `PSModulePath` variable d’environnement stocke les chemins d’accès aux emplacements des modules installés sur le disque. PowerShell utilise cette variable pour localiser les modules lorsque l’utilisateur ne spécifie pas le chemin d’accès complet à un module. Les chemins d’accès de cette variable sont recherchés dans l’ordre dans lequel ils apparaissent.

Lorsque PowerShell démarre, `PSModulePath` est créé en tant que variable d’environnement système avec la valeur par défaut suivante : `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` sur Windows et `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` sur Linux ou Mac, et `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` pour Windows PowerShell.

> [!NOTE]
> L’emplacement **CurrentUser** propre à l’utilisateur est le `WindowsPowerShell\Modules` dossier situé à l’emplacement **documents** dans votre profil utilisateur. Le chemin d’accès spécifique de cet emplacement varie selon la version de Windows et si vous utilisez la redirection de dossiers ou non. Par défaut, sur Windows 10, cet emplacement est `$HOME\Documents\WindowsPowerShell\Modules` .

## <a name="to-view-the-psmodulepath-variable"></a>Pour afficher la variable PSModulePath

Pour afficher les chemins d’accès spécifiés dans la `PSModulePath` variable, tapez la commande suivante :

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>Pour ajouter des emplacements à la variable PSModulePath

Pour ajouter des chemins d’accès à cette variable, utilisez l’une des méthodes suivantes :

- Pour ajouter une valeur temporaire qui est uniquement disponible pour la session active, exécutez la commande suivante sur la ligne de commande :

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- Pour ajouter une valeur persistante qui est disponible chaque fois qu’une session est ouverte, ajoutez la commande ci-dessus à un fichier de profil PowerShell ( `$PROFILE` ) >

  Pour plus d'informations sur les profils, consultez [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).

- Pour ajouter une variable persistante au registre, créez une nouvelle variable d’environnement utilisateur appelée `PSModulePath` à l’aide de l’éditeur de variables d’environnement dans la boîte de dialogue **Propriétés système** .

- Pour ajouter une variable persistante à l’aide d’un script, utilisez la méthode .NET [SetEnvironmentVariable ne contient](/dotnet/api/system.environment.setenvironmentvariable) sur la classe [System. Environment](/dotnet/api/system.environment) . Par exemple, le script suivant ajoute le `C:\Program Files\Fabrikam\Module` chemin d’accès à la valeur de la `PSModulePath` variable d’environnement pour l’ordinateur. Pour ajouter le chemin d’accès à la `PSModulePath` variable d’environnement utilisateur, définissez la cible sur « User ».

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>Pour supprimer des emplacements du PSModulePath

Vous pouvez supprimer les chemins d’accès de la variable à l’aide de méthodes similaires : par exemple, `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` supprime le chemin d’accès **c:\ModulePath** de la session active.

## <a name="see-also"></a>Voir aussi

[Écriture d’un module Windows PowerShell](./writing-a-windows-powershell-module.md)

[about_Modules](/powershell/module/microsoft.powershell.core/about/about_modules)
