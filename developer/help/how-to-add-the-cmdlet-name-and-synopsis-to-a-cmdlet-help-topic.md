---
title: Comment ajouter le nom de l’applet de commande et le Synopsis à une rubrique d’aide applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083331"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a>Guide pratique pour ajouter le nom de l’applet de commande et le synopsis à une rubrique d’aide d’une applet de commande

Cette section décrit comment ajouter du contenu qui s’affiche dans les sections nom et le résumé de l’aide de l’applet de commande. Dans le fichier d’aide, ce contenu est ajouté au nœud de commande pour chaque applet de commande.

> [!NOTE]
> Pour obtenir une vue complète d’un fichier d’aide, ouvrez un des fichiers dll-Help.xml situé dans le répertoire d’installation de Windows PowerShell. Par exemple, le fichier Microsoft.PowerShell.Commands.Management.dll-Help.xml contient le contenu pour plusieurs des applets de commande Windows PowerShell.

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a>Pour ajouter le nom de l’applet de commande et un résumé

- L’applet de commande aide peut afficher deux descriptions de l’applet de commande. La première description est une brève description qui est appelée le synopsis. La seconde description est une description plus détaillée est décrite dans [Ajout de la Description détaillée pour une rubrique d’aide applet de commande](./how-to-add-a-cmdlet-description.md). Les deux de ces descriptions devraient être écrit comme un seul paragraphe.

- Le résumé ne se répètent pas le nom de l’applet de commande. Pour informer l’utilisateur que l’applet de commande Get-serveur obtient un serveur est courte, mais pas informatives. À la place, utiliser des synonymes et ajouter des détails à la description.

  Exemple : « Obtient un objet qui représente un ordinateur local ou distant. »

- Utiliser des verbes simples comme « get », « créer » et « modifier » dans le résumé. Évitez d’utiliser « set », car il est vague et fantaisistes mots tels que « modifier. »

  Exemple : « Obtient des informations sur la signature Authenticode dans un fichier ».

- Écrire dans la voix active. Par exemple, « utiliser l’objet TimeSpan... » est beaucoup plus claire que « l’objet TimeSpan peut être utilisé pour... »

- Évitez le verbe « affichage » lors de la description des applets de commande permettant d’obtenir des objets. Bien que Windows PowerShell affiche des données de l’applet de commande, il est important présenter le concept de l’applet de commande retourne les objets .NET Framework dont les données ne peuvent pas s’afficher aux utilisateurs. Si vous mettre l’accent sur l’affichage, l’utilisateur peut-être ignorer que l’applet de commande a peut-être retourné nombreuses autres propriétés et méthodes utiles qui ne sont pas affichés.

## <a name="see-also"></a>Voir aussi

 [Windows PowerShell SDK](../windows-powershell-reference.md)