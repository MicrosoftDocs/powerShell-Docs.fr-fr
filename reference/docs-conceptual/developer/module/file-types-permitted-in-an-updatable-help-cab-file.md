---
title: Types de fichiers autorisés dans un fichier CAB d’aide pouvant être mis à jour | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: acabdb93-c41a-4b8d-acbe-45cdab91e198
caps.latest.revision: 10
ms.openlocfilehash: 6e9e51a50226430465726d27874e02e98ee67672
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560982"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a>Types de fichiers autorisés dans un fichier CAB d’aide actualisable

Cette rubrique répertorie et décrit la configuration requise pour le contenu des fichiers CAB de l’aide actualisable.

## <a name="updatable-help-cab-file-requirements"></a>Configuration requise pour le fichier CAB de l’aide actualisable

Le contenu du fichier CAB non compressé est limité à 1 Go par défaut. Pour contourner cette limite, les utilisateurs doivent utiliser le paramètre **force** des applets de commande [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) et [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) .

Pour garantir la sécurité des fichiers d’aide téléchargés à partir d’Internet, un fichier CAB d’aide pouvant être mis à jour peut inclure uniquement les types de fichiers répertoriés ci-dessous. L’applet de commande [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) valide tous les fichiers par rapport aux schémas de rubrique d’aide. Si l' `Update-Help` applet de commande rencontre un fichier qui n’est pas valide ou n’est pas un type autorisé, elle n’installe pas le fichier non valide et arrête l’installation des fichiers à partir du fichier cab sur l’ordinateur de l’utilisateur.

- Rubriques d’aide XML pour les applets de commande.

- Rubriques d’aide XML pour les scripts et les fonctions.

- Rubriques d’aide XML pour les fournisseurs Windows PowerShell.

- Rubriques d’aide textuelles, telles que les rubriques à propos de.

La [mise à jour-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) vérifie le contenu du fichier CAB lorsqu’il décompresse le fichier CAB. Si `Update-Help` recherche des types de fichiers non conformes dans un fichier cab d’aide actualisable, il génère une erreur de fin et arrête l’opération. Il n’installe pas les fichiers d’aide à partir du fichier CAB, même ceux des types de fichiers conformes.
