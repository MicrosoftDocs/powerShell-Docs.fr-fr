---
title: Fichier CAB d’aider à des Types de fichiers autorisés dans un actualisable | Microsoft Docs
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
ms.openlocfilehash: 3562804157ebdfca561445a8671d726b55cc4efd
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794244"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a>Types de fichiers autorisés dans un fichier CAB d’aide actualisable

Cette rubrique répertorie et décrit les exigences de contenu pour les fichiers CAB de vous aider à être mise à jour.

## <a name="updatable-help-cab-file-requirements"></a>Configuration requise du fichier CAB aide actualisable

Contenu du fichier CAB non compressé est limité à 1 Go par défaut. Pour contourner cette limite, les utilisateurs doivent utiliser le **Force** paramètre de la [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) et [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) applets de commande.

Afin de garantir la sécurité des fichiers d’aide qui sont téléchargés à partir d’Internet, un fichier CAB d’aide actualisable peut inclure uniquement les types de fichiers répertoriés ci-dessous. Le [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) applet de commande valide tous les fichiers par rapport aux schémas de la rubrique d’aide. Si le `Update-Help` applet de commande rencontre un fichier qui n’est pas valide ou n’est pas un type autorisé, il n’installe pas le fichier non valide et arrête l’installation des fichiers du fichier cab sur l’ordinateur de l’utilisateur.

- Rubriques d’aide basé sur XML pour les applets de commande.

- Rubriques d’aide basé sur XML pour les scripts et fonctions.

- Rubriques d’aide basé sur XML pour les fournisseurs Windows PowerShell.

- Textuel rubriques d’aide, telles que sur des sujets.

Le [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) vérifie le contenu du fichier CAB lorsqu’il décompresse le fichier CAB. Si `Update-Help` recherche les types de fichier non conforme dans un fichier CAB d’aide actualisable, il génère une erreur avec fin d’exécution et arrête l’opération. Il n’installe pas les fichiers d’aide du fichier CAB, y compris celles des types de fichier compatible.