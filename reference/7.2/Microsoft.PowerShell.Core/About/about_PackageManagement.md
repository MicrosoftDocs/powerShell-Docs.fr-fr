---
description: PackageManagement est un agrégateur pour les gestionnaires de packages de logiciels.
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_packagemanagement?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PackageManagement
ms.openlocfilehash: 22f47d01063778fca4f51a534b15d485b3beee28
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603652"
---
# <a name="about-packagemanagement"></a>À propos de PackageManagement

## <a name="short-description"></a>DESCRIPTION COURTE
PackageManagement est un agrégateur pour les gestionnaires de packages de logiciels.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

La fonctionnalité PackageManagement a été introduite dans Windows PowerShell 5,0.

PackageManagement est une interface unifiée pour les systèmes de gestion des packages logiciels ; vous pouvez exécuter les applets de commande PackageManagement pour effectuer des tâches de détection, d’installation et d’inventaire de logiciels (gestion). Quelle que soit la technologie d’installation sous-jacente, vous pouvez exécuter les applets de commande courantes dans le module PackageManagement pour rechercher, installer ou désinstaller des packages. Ajouter, supprimer et interroger des dépôts de packages ; et exécuter des requêtes sur un ordinateur pour déterminer quels packages logiciels sont installés.

PackageManagement prend en charge un modèle de plug-in flexible qui permet la prise en charge d’autres systèmes de gestion de packages logiciels.

Le module PackageManagement est inclus dans Windows PowerShell 5,0 et versions ultérieures de PowerShell, et fonctionne sur trois niveaux de la structure de gestion des packages : les fournisseurs de package, les sources de package et les packages eux-mêmes. Nous allons définir des termes :

- Gestionnaire de package : système de gestion des packages logicielles. En termes de PackageManagement, il s’agit d’un fournisseur de package.
- Fournisseur de package : terme PackageManagement pour un gestionnaire de package. Les exemples peuvent inclure des Windows Installer, du chocolat et d’autres.
- Source du package : URL, dossier local ou dossier partagé sur le réseau que vous configurez en tant que référentiel à l’aide des fournisseurs de package.
- Package : élément logiciel géré par un fournisseur de package et stocké dans une source de package spécifique.

Le module PackageManagement comprend les applets de commande suivantes. Pour plus d’informations, consultez l’aide de [PackageManagement](/powershell/module/packagemanagement) .

- `Get-PackageProvider`: Retourne la liste des fournisseurs de packages qui sont connectés à PackageManagement.
- `Get-PackageSource`: Obtient la liste des sources de packages qui sont inscrites pour un fournisseur de package.
- `Register-PackageSource`: Ajoute une source de package pour un fournisseur de package spécifié.
- `Set-PackageSource`: Définit les propriétés sur une source de package existante.
- `Unregister-PackageSource`: Supprime une source de package inscrite.
- `Get-Package`: Retourne la liste des packages de logiciels installés.
- `Find-Package`: Recherche les packages de logiciels dans les sources de package disponibles.
- `Install-Package`: Installe un ou plusieurs packages logiciels.
- `Save-Package`: Enregistre les packages sur l’ordinateur local sans les installer.
- `Uninstall-Package`: Désinstalle un ou plusieurs packages logiciels.

### <a name="package-provider-bootstrapping-and-dynamic-cmdlet-parameters"></a>Paramètres d’applet de commande dynamique et d’amorçage du fournisseur de package

Par défaut, PackageManagement est fourni avec un fournisseur de démarrage principal. Vous pouvez installer des fournisseurs de packages supplémentaires en fonction de vos besoins en amorceant les fournisseurs. autrement dit, réponse à une invite pour installer le fournisseur automatiquement à partir d’un service Web. Vous pouvez spécifier un fournisseur de package avec n’importe quelle applet de commande PackageManagement. Si le fournisseur spécifié n’est pas disponible, PackageManagement vous invite à démarrer (ou à installer automatiquement) le fournisseur. Dans les exemples suivants, si le fournisseur de chocolat n’est pas déjà installé, le programme d’amorçage PackageManagement installe le fournisseur.

```powershell
Find-Package -Provider Chocolatey <PackageName>
```

Si le fournisseur de chocolat n’est pas déjà installé, lorsque vous exécutez la commande précédente, vous êtes invité à l’installer.

```powershell
Install-Package <Chocolatey package Name> -ForceBootstrap
```

Si le fournisseur de chocolat n’est pas déjà installé, lorsque vous exécutez la commande précédente, le fournisseur est installé. Toutefois, étant donné que le paramètre ForceBootstrap a été ajouté à la commande, vous n’êtes pas invité à l’installer. le fournisseur et le package sont tous deux installés automatiquement.

Lorsque vous essayez d’installer un package, si le fournisseur de prise en charge n’est pas déjà installé et que vous n’ajoutez pas le paramètre ForceBootstrap à votre commande, PackageManagement vous invite à installer le fournisseur.

La spécification d’un fournisseur de package dans votre commande PackageManagement peut rendre les paramètres dynamiques disponibles qui sont spécifiques à ce fournisseur de package. Lorsque vous exécutez Get-Help pour une applet de commande PackageManagement spécifique, une liste de jeux de paramètres est retournée, en regroupant les paramètres dynamiques des fournisseurs de packages disponibles dans des jeux de paramètres distincts.

Plus d’informations sur le projet PackageManagement

Pour plus d’informations sur le projet de développement PackageManagement ouvert, notamment sur la création d’un fournisseur de packages PackageManagement, consultez le projet PackageManagement sur GitHub à l’adresse https://oneget.org .

## <a name="see-also"></a>VOIR AUSSI

[Get-PackageProvider](xref:PackageManagement.Get-PackageProvider)

[Get-PackageSource](xref:PackageManagement.Get-PackageSource)

[Register-PackageSource](xref:PackageManagement.Register-PackageSource)

[Set-PackageSource](xref:PackageManagement.Set-PackageSource)

[Unregister-PackageSource](xref:PackageManagement.Unregister-PackageSource)

[Get-Package](xref:PackageManagement.Get-Package)

[Find-Package](xref:PackageManagement.Find-Package)

[Install-Package](xref:PackageManagement.Install-Package)

[Save-Package](xref:PackageManagement.Save-Package)

[Uninstall-Package](xref:PackageManagement.Uninstall-Package)

