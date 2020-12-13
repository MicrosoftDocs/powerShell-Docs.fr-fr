---
ms.date: 03/22/2012
ms.topic: reference
title: Types de fichiers autorisés dans un fichier CAB d’aide actualisable
description: Types de fichiers autorisés dans un fichier CAB d’aide actualisable
ms.openlocfilehash: bb69b8b89a9a3a5c8c00059ec404a4d41a5db9a5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654746"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a>Types de fichiers autorisés dans un fichier CAB d’aide actualisable

Le contenu du fichier CAB non compressé est limité à 1 Go par défaut. Pour contourner cette limite, les utilisateurs doivent utiliser le paramètre **force** des applets de commande [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) et [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) .

Pour garantir la sécurité des fichiers d’aide téléchargés à partir d’Internet, un fichier CAB d’aide pouvant être mis à jour peut inclure uniquement les types de fichiers répertoriés ci-dessous. L’applet de commande [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) valide tous les fichiers par rapport aux schémas de rubrique d’aide. Si l' `Update-Help` applet de commande rencontre un fichier qui n’est pas valide ou n’est pas un type autorisé, elle n’installe pas le fichier non valide et arrête l’installation des fichiers à partir du fichier cab sur l’ordinateur de l’utilisateur.

- Rubriques d’aide XML pour les applets de commande.
- Rubriques d’aide XML pour les scripts et les fonctions.
- Rubriques d’aide XML pour les fournisseurs PowerShell.
- Rubriques d’aide textuelles, telles que les rubriques à propos de.

La [mise à jour-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) vérifie le contenu du fichier CAB lorsqu’il décompresse le fichier CAB. Si `Update-Help` recherche des types de fichiers non conformes dans un fichier cab d’aide actualisable, il génère une erreur de fin et arrête l’opération. Il n’installe pas les fichiers d’aide à partir du fichier CAB, même ceux des types de fichiers conformes.
