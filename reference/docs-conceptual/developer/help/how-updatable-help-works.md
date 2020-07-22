---
title: Fonctionnement de l’aide actualisable
ms.date: 09/13/2016
ms.openlocfilehash: 4849ce81e31171c6822a9078a77ebb45729185a3
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893286"
---
# <a name="how-updatable-help-works"></a>Fonctionnement de l’aide actualisable

Cette rubrique explique comment mettre à jour l’aide pour traiter le fichier XML et les fichiers CAB HelpInfo pour chaque module, et comment installer l’aide mise à jour pour les utilisateurs.

## <a name="the-update-help-process"></a>Processus de mise à jour-aide

La liste suivante décrit les actions de l’applet de commande [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) lorsqu’un utilisateur exécute une commande pour mettre à jour les fichiers d’aide d’un module dans une culture d’interface utilisateur particulière.

1. `Update-Help`Obtient le fichier XML HelpInfo distant à partir de l’emplacement spécifié par la valeur de la clé **HelpInfoURI** dans le manifeste de module et valide le fichier par rapport au schéma. (Pour afficher le schéma, consultez [schéma XML HelpInfo](./helpinfo-xml-schema.md).) `Update-Help`Recherche ensuite un fichier XML HelpInfo local pour le module dans le répertoire du module sur l’ordinateur de l’utilisateur.

1. `Update-Help`compare le numéro de version des fichiers d’aide pour la culture d’interface utilisateur spécifiée dans les fichiers HelpInfo XML distants et locaux pour le module. Si le numéro de version du fichier distant est supérieur au numéro de version du fichier local, ou s’il n’existe aucun fichier XML HelpInfo local pour le module, `Update-Help` prépare le téléchargement des nouveaux fichiers d’aide.

1. `Update-Help`sélectionne le fichier CAB pour le module à partir de l’emplacement spécifié par l’élément **HelpContentUri** dans le fichier XML HelpInfo distant. Elle utilise le nom du module, le GUID du module et la culture de l’interface utilisateur pour identifier le fichier CAB.

1. `Update-Help`télécharge le fichier CAB, le décompresse, valide les fichiers de contenu d’aide et enregistre les fichiers de contenu d’aide dans le sous-répertoire spécifique à la langue du répertoire du module sur l’ordinateur de l’utilisateur.

1. `Update-Help`crée un fichier XML HelpInfo local en copiant le fichier XML HelpInfo distant. Elle modifie le fichier XML HelpInfo local afin qu’il inclue uniquement des éléments pour le fichier CAB qu’il a installé.
   Ensuite, il enregistre le fichier XML HelpInfo local dans le répertoire du module et termine la mise à jour.

## <a name="the-save-help-process"></a>Processus Save-Help

La liste suivante décrit les actions des applets de commande [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) et [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) lorsqu’un utilisateur exécute des commandes pour mettre à jour les fichiers d’aide dans un partage de fichiers, puis utiliser ces fichiers pour mettre à jour les fichiers d’aide sur l’ordinateur de l’utilisateur.

L' `Save-Help` applet de commande effectue les actions suivantes en réponse à une commande pour enregistrer les fichiers d’aide d’un module dans un partage de fichiers spécifié par le paramètre **DestinationPath** .

1. `Save-Help`Obtient le fichier XML HelpInfo distant à partir de l’emplacement spécifié par la valeur de la clé **HelpInfoURI** dans le manifeste de module et valide le fichier par rapport au schéma. (Pour afficher le schéma, consultez [schéma XML HelpInfo](./helpinfo-xml-schema.md).) `Save-Help`Recherche ensuite un fichier XML HelpInfo local dans le répertoire spécifié par le paramètre **DestinationPath** dans la `Save-Help` commande.

1. `Save-Help`compare le numéro de version des fichiers d’aide pour la culture d’interface utilisateur spécifiée dans les fichiers HelpInfo XML distants et locaux pour le module. Si le numéro de version du fichier distant est supérieur au numéro de version du fichier local, ou s’il n’existe aucun fichier XML HelpInfo local pour le module dans le répertoire **DestinationPath** , `Save-Help` prépare le téléchargement des nouveaux fichiers d’aide.

1. `Save-Help`sélectionne le fichier CAB pour le module à partir de l’emplacement spécifié par l’élément **HelpContentUri** dans le fichier XML HelpInfo distant. Elle utilise le nom du module, le GUID du module et la culture de l’interface utilisateur pour identifier le fichier CAB.

1. `Save-Help`télécharge le fichier CAB et l’enregistre dans le répertoire **DestinationPath** . (Elle ne crée pas de sous-répertoires spécifiques à une langue.)

1. `Save-Help`crée un fichier XML HelpInfo local en copiant le fichier XML HelpInfo distant. Elle modifie le fichier XML HelpInfo local afin qu’il inclue uniquement des éléments pour le fichier CAB qu’il a enregistré.
   Ensuite, il enregistre le fichier XML HelpInfo local dans le répertoire **DestinationPath** et termine la mise à jour.

   L' `Update-Help` applet de commande effectue les actions suivantes en réponse à une commande pour mettre à jour les fichiers d’aide sur l’ordinateur d’un utilisateur à partir des fichiers d’un partage de fichiers qui est spécifié par le paramètre **SourcePath** .

1. `Update-Help`Obtient le fichier XML HelpInfo distant à partir du répertoire **SourcePath** . Il recherche ensuite un fichier XML HelpInfo local dans le répertoire du module sur l’ordinateur de l’utilisateur.

1. `Update-Help`compare le numéro de version des fichiers d’aide pour la culture d’interface utilisateur spécifiée dans les fichiers HelpInfo XML distants et locaux pour le module. Si le numéro de version du fichier distant est supérieur au numéro de version du fichier local, ou s’il n’existe aucun fichier XML HelpInfo local, `Update-Help` prépare l’installation de nouveaux fichiers d’aide.

1. `Update-Help`sélectionne le fichier CAB du module dans le répertoire **SourcePath** . Elle utilise le nom du module, le GUID du module et la culture de l’interface utilisateur pour identifier le fichier CAB.

1. `Update-Help`décompresse le fichier CAB, valide les fichiers de contenu d’aide et enregistre les fichiers de contenu d’aide dans le sous-répertoire spécifique à la langue du répertoire du module sur l’ordinateur de l’utilisateur.

1. `Update-Help`crée un fichier XML HelpInfo local en copiant le fichier XML HelpInfo distant. Elle modifie le fichier XML HelpInfo local afin qu’il inclue uniquement des éléments pour le fichier CAB qu’il a installé.
   Ensuite, il enregistre le fichier XML HelpInfo local dans le répertoire du module et termine la mise à jour.
