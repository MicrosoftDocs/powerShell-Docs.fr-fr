---
title: Comment ajouter le nom de l’applet de commande et synopsis à une rubrique d’aide sur une applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361188"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a>Guide pratique pour ajouter le nom de l’applet de commande et le synopsis à une rubrique d’aide d’une applet de commande

Cette section décrit comment ajouter du contenu qui s’affiche dans les sections nom et SYNOPSIS de l’aide de l’applet de commande. Dans le fichier d’aide, ce contenu est ajouté au nœud de commande pour chaque applet de commande.

> [!NOTE]
> Pour obtenir une vue complète d’un fichier d’aide, ouvrez l’un des fichiers dll-Help. XML qui se trouvent dans le répertoire d’installation de Windows PowerShell. Par exemple, le fichier Microsoft. PowerShell. Commands. Management. dll-Help. xml contient du contenu pour plusieurs des applets de commande Windows PowerShell.

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a>Pour ajouter le nom de l’applet de commande et un Synopsis

- L’aide de l’applet de commande peut afficher deux descriptions pour l’applet de commande. La première description est une brève description, appelée Synopsis. La deuxième Description est une description plus détaillée qui est décrite dans [Ajout de la description détaillée à une rubrique d’aide sur une applet](./how-to-add-a-cmdlet-description.md)de commande. Ces deux descriptions doivent être écrites sous la forme d’un seul paragraphe.

- Dans le synopsis, ne répétez pas le nom de l’applet de commande. Informant l’utilisateur que l’applet de commande obtenir-Server obtient un serveur est brève, mais pas informatif. Utilisez plutôt des synonymes et ajoutez des détails à la description.

  Exemple : « obtient un objet qui représente un ordinateur local ou distant ».

- Utilisez des verbes simples tels que « obten », « Create » et « change » dans le synopsis. Évitez d’utiliser « SET », car il est vague et des mots fantaisie tels que « modifier ».

  Exemple : "obtient des informations sur la signature Authenticode dans un fichier."

- Écrire dans la voix active. Par exemple, « utiliser l’objet TimeSpan... » est plus clair que « l’objet TimeSpan peut être utilisé pour... »

- Évitez le verbe « Display » lors de la description des applets de commande qui obtiennent des objets. Bien que Windows PowerShell affiche les données des applets de commande, il est important d’introduire les utilisateurs au concept que l’applet de commande renvoie .NET Framework objets dont les données peuvent ne pas être affichées. Si vous insistez sur l’affichage, l’utilisateur peut ne pas se rendre compte que l’applet de commande a peut-être retourné de nombreuses autres propriétés et méthodes utiles qui ne sont pas affichées.

## <a name="see-also"></a>Voir aussi

 [Windows PowerShell SDK](../windows-powershell-reference.md)