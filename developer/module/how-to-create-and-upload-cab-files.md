---
title: Comment créer et télécharger des fichiers CAB | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d35f233-5447-48a2-a961-9fbca763262b
caps.latest.revision: 7
ms.openlocfilehash: 9928a0b31a57d42eb39cea1af0509613c483caf7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082377"
---
# <a name="how-to-create-and-upload-cab-files"></a>Guide pratique pour créer et charger des fichiers CAB

Cette rubrique explique comment créer des fichiers CAB de vous aider à être mises à jour et les télécharger à l’emplacement où les applets de commande de l’aide actualisable peut les trouver.

## <a name="how-to-create-and-upload-updatable-help-cab-files"></a>Comment créer et charger des fichiers CAB d’aide actualisable

Vous pouvez utiliser la fonctionnalité d’aide actualisable pour distribuer des fichiers nouveaux ou mis à jour à l’aide d’un module dans plusieurs langues et cultures. Un package pour un module d’aide actualisable se compose d’un fichier XML HelpInfo et un ou plusieurs armoire (. Fichiers CAB). Chaque fichier CAB contient les fichiers d’aide pour le module dans une culture d’interface utilisateur. Utilisez la procédure suivante pour créer des fichiers CAB pour vous aider à être mise à jour.

1. Organiser les fichiers d’aide pour le module par culture d’interface utilisateur. Chaque fichier CAB d’aide actualisable contient les fichiers d’aide pour un module dans une culture d’interface utilisateur. Vous pouvez remettre aide de plusieurs fichiers CAB pour le module, chacun d’eux pour une autre culture d’interface utilisateur.

2. Vérifiez que les fichiers d’aide incluent uniquement les types de fichiers autorisés pour vous aider à être mises à jour et de les valider par rapport à un schéma de fichier d’aide. Si le `Update-Help` applet de commande rencontre un fichier qui n’est pas valide ou n’est pas un type autorisé, il n’installe pas le fichier non valide et arrête l’installation des fichiers à partir du fichier CAB. Pour obtenir la liste des types de fichiers autorisés, consultez [fichier Types autorisés dans un fichier CAB d’aide actualisable](./file-types-permitted-in-an-updatable-help-cab-file.md).

3. Signer numériquement les fichiers d’aide. Signatures numériques ne sont pas nécessaires, mais ils sont une bonne pratique.

4. Incluent l’ensemble de l’aide de fichiers pour le module dans l’interface utilisateur de culture, non seulement les fichiers qui sont nouveaux ou ont été modifiés. Si le fichier CAB est incomplète, les utilisateurs téléchargement des fichiers d’aide pour la première fois ou de ne pas téléchargent de chaque mise à jour aura pas tous les fichiers d’aide de module.

5. Utiliser un utilitaire qui crée des fichiers CAB, telles que MakeCab.exe. Windows PowerShell n’inclut pas les applets de commande qui créent des fichiers CAB.

6. Nommez les fichiers CAB. Pour plus d’informations, consultez [le nom d’un fichier CAB d’aide actualisable](./how-to-name-an-updatable-help-cab-file.md).

7. Télécharger les fichiers CAB pour le module à l’emplacement spécifié par le **HelpContentUri** élément dans le fichier XML HelpInfo du module. Puis chargez le fichier XML HelpInfo à l’emplacement spécifié par le **HelpInfoUri** clés du manifeste du module. Le **HelpContentUri** et **HelpInfoUri** peut pointer vers le même emplacement.

> [!CAUTION]
> La valeur de la **HelpInfoUri** clé et le **HelpContentUri** élément doit commencer par « http » ou « https ». La valeur doit indiquer un emplacement Internet et ne doit pas inclure un nom de fichier.