---
title: Comment mettre à jour Help opère | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7674636e-a0f2-4587-bfc5-dd3e6ce5489e
caps.latest.revision: 6
ms.openlocfilehash: 8874cc18416937c4d3cb30d801f2714410304c8c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860875"
---
# <a name="how-updatable-help-works"></a>Fonctionnement de l’aide actualisable

Cette rubrique explique comment un processus de l’aide actualisable le fichier XML HelpInfo CAB les fichiers pour chaque module et installe aide mis à jour pour les utilisateurs.

## <a name="the-update-help-process"></a>Le processus de mise à jour-Help

Le tableau suivant répertorie les actions de la [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) applet de commande lorsqu’un utilisateur exécute une commande pour mettre à jour les fichiers d’aide pour un module dans une culture d’interface utilisateur particulier.
Le tableau suivant répertorie les actions de la [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) applet de commande lorsqu’un utilisateur exécute une commande pour mettre à jour les fichiers d’aide pour un module dans une culture d’interface utilisateur particulier.

1. `Update-Help` Obtient le fichier XML HelpInfo à distance à partir de l’emplacement spécifié par la valeur de la **HelpInfoURI** de clé dans le manifeste de module et valide le fichier par rapport au schéma. (Pour afficher le schéma, consultez [HelpInfo XML Schema](./helpinfo-xml-schema.md).) Puis `Update-Help` recherche un fichier XML HelpInfo local pour le module dans le répertoire de module sur l’ordinateur de l’utilisateur.

2. `Update-Help` Compare le numéro de version des fichiers d’aide pour la culture d’interface utilisateur spécifiée dans les fichiers XML HelpInfo locaux et distants pour le module. Si le numéro de version sur le fichier distant est supérieur au numéro de version sur le fichier local, ou s’il n’existe aucun fichier XML HelpInfo local pour le module, `Update-Help` se prépare à télécharger de nouveaux fichiers d’aide.

3. `Update-Help` Sélectionne le fichier CAB pour le module à partir de l’emplacement spécifié par le **HelpContentUri** élément dans le fichier XML HelpInfo à distance. Il utilise le nom du module, le GUID du module et la culture d’interface utilisateur pour identifier le fichier CAB.

4. `Update-Help` télécharge le fichier CAB, il décompresse, valide les fichiers de contenu d’aide et les enregistre à l’aide de fichiers de contenu dans le sous-répertoire spécifique au langage du répertoire du module sur l’ordinateur de l’utilisateur.

5. `Update-Help` Crée un fichier XML HelpInfo local en copiant le fichier XML HelpInfo à distance. Il modifie le fichier XML HelpInfo local afin qu’il inclue des éléments uniquement pour le fichier CAB qu’il a installés. Ensuite, il enregistre le fichier XML HelpInfo local dans le répertoire de module et conclut la mise à jour.

## <a name="the-save-help-process"></a>Le processus de Save-Help

Le tableau suivant répertorie les actions de la [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) et [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) applets de commande lorsqu’un utilisateur exécute des commandes pour mettre à jour les fichiers d’aide dans un partage de fichiers, puis utiliser ces fichiers pour mettre à jour les fichiers d’aide sur la ordinateur de l’utilisateur.
Le tableau suivant répertorie les actions de la [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) et [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) applets de commande lorsqu’un utilisateur exécute des commandes pour mettre à jour les fichiers d’aide dans un partage de fichiers, puis utiliser ces fichiers pour mettre à jour les fichiers d’aide sur la ordinateur de l’utilisateur.

Le `Save-Help` applet de commande effectue les actions suivantes en réponse à une commande pour enregistrer les fichiers d’aide pour un module dans un partage de fichiers spécifié par le **DestinationPath** paramètre.

1. `Save-Help` Obtient le fichier XML HelpInfo à distance à partir de l’emplacement spécifié par la valeur de la **HelpInfoURI** de clé dans le manifeste de module et valide le fichier par rapport au schéma. (Pour afficher le schéma, consultez [HelpInfo XML Schema](./helpinfo-xml-schema.md).) Puis `Save-Help` recherche un fichier XML HelpInfo local dans le répertoire spécifié par le **DestinationPath** paramètre dans le `Save-Help` commande.

2. `Save-Help` Compare le numéro de version des fichiers d’aide pour la culture d’interface utilisateur spécifiée dans les fichiers XML HelpInfo locaux et distants pour le module. Si le numéro de version sur le fichier distant est supérieur au numéro de version sur le fichier local, ou s’il n’existe aucun fichier XML HelpInfo local pour le module dans le **DestinationPath** directory, `Save-Help` se prépare à télécharger de nouveaux fichiers d’aide.

3. `Save-Help` Sélectionne le fichier CAB pour le module à partir de l’emplacement spécifié par le **HelpContentUri** élément dans le fichier XML HelpInfo à distance. Il utilise le nom du module, le GUID du module et la culture d’interface utilisateur pour identifier le fichier CAB.

4. `Save-Help` télécharge le fichier CAB et l’enregistre dans le **DestinationPath** directory. (Il ne crée pas les sous-répertoires spécifiques au langage.)

5. `Save-Help` Crée un fichier XML HelpInfo local en copiant le fichier XML HelpInfo à distance. Il modifie le fichier XML HelpInfo local afin qu’il inclue des éléments uniquement pour le fichier CAB qu’il a enregistrée. Ensuite, elle enregistre le fichier XML HelpInfo local dans le **DestinationPath** répertoire et se termine la mise à jour.

   Le `Update-Help` applet de commande effectue les actions suivantes en réponse à une commande pour mettre à jour les fichiers d’aide sur l’ordinateur d’un utilisateur à partir des fichiers dans un partage de fichiers spécifié par le **SourcePath** paramètre.

1. `Update-Help` Obtient le fichier XML HelpInfo à distance à partir de la **SourcePath** directory. Puis il recherche un fichier XML HelpInfo local dans le répertoire de module sur l’ordinateur de l’utilisateur.

2. `Update-Help` Compare le numéro de version des fichiers d’aide pour la culture d’interface utilisateur spécifiée dans les fichiers XML HelpInfo locaux et distants pour le module. Si le numéro de version sur le fichier distant est supérieur au numéro de version sur le fichier local, ou s’il n’existe aucun fichier XML HelpInfo local, `Update-Help` prépare l’installation de nouveaux fichiers d’aide.

3. `Update-Help` Sélectionne le fichier CAB pour le module à partir de **SourcePath** directory. Il utilise le nom du module, le GUID du module et la culture d’interface utilisateur pour identifier le fichier CAB.

4. `Update-Help` décompresse le fichier CAB, valide les fichiers de contenu d’aide et enregistre à l’aide de fichiers de contenu dans le sous-répertoire spécifique au langage du répertoire du module sur l’ordinateur de l’utilisateur.

5. `Update-Help` Crée un fichier XML HelpInfo local en copiant le fichier XML HelpInfo à distance. Il modifie le fichier XML HelpInfo local afin qu’il inclue des éléments uniquement pour le fichier CAB qu’il a installés. Ensuite, il enregistre le fichier XML HelpInfo local dans le répertoire de module et conclut la mise à jour.