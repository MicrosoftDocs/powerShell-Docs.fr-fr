---
title: Comment créer le fichier d’aide de l’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858975"
---
# <a name="how-to-create-the-cmdlet-help-file"></a>Guide pratique pour créer le fichier d’aide d’une applet de commande

Cette section décrit comment créer un fichier XML valide qui contient le contenu des rubriques d’aide applet de commande Windows PowerShell. Cette section explique comment nommer le fichier d’aide, comment ajouter les en-têtes XML appropriés et comment ajouter des nœuds qui contiendront les différentes sections de contenu de l’aide de l’applet de commande.

> [!NOTE]
> Pour obtenir une vue complète d’un fichier d’aide, ouvrez un des fichiers dll-Help.xml situé dans le répertoire d’installation de Windows PowerShell. Par exemple, le fichier Microsoft.PowerShell.Commands.Management.dll-Help.xml contient le contenu pour plusieurs des applets de commande Windows PowerShell.

### <a name="how-to-create-a-cmdlet-help-file"></a>Comment créer un fichier d’aide de l’applet de commande

1. Créez un fichier texte et enregistrez-le à l’aide de l’encodage UTF8. Le nom de fichier doit avoir le format suivant pour que Windows PowerShell puisse le détecter en tant qu’un fichier d’aide applet de commande.

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. Ajoutez les en-têtes XML suivants au fichier texte. N’oubliez pas que le fichier sera être validé par rapport au schéma de langage de modélisation multi-agent (MAML). Actuellement, Windows PowerShell ne fournit pas d’outils pour valider le fichier.

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. Ajouter un nœud de commande pour chaque applet de commande dans l’assembly dans le fichier d’aide de l’applet de commande. Chaque nœud dans le nœud commande concerne les différentes sections de la rubrique d’aide de l’applet de commande.

   Le tableau suivant répertorie l’élément XML pour chaque nœud, suivie d’une description de chaque nœud.

   |Nœud|Description|
   |----------|-----------------|
   |`<details>`|Ajoute du contenu pour les sections nom et le résumé de la rubrique d’aide applet de commande. Pour plus d’informations, consultez [comment ajouter le nom de l’applet de commande et le Synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).|
   |`<maml:description>`|Ajoute du contenu de la section DESCRIPTION de la rubrique d’aide de l’applet de commande. Pour plus d’informations, consultez [comment ajouter la Description détaillée pour une rubrique d’aide applet de commande](./how-to-add-a-cmdlet-description.md).|
   |`<command:syntax>`|Ajoute le contenu de la section syntaxe de la rubrique d’aide de l’applet de commande. Pour plus d’informations, consultez [comment la syntaxe de l’ajouter à une rubrique d’aide applet de commande](./how-to-add-syntax-to-a-cmdlet-help-topic.md).|
   |`<command:parameters>`|Ajoute du contenu de la section Paramètres de rubrique d’aide de l’applet de commande. Pour plus d’informations, consultez [comment ajouter des paramètres à une rubrique d’aide applet de commande](./how-to-add-parameter-information.md).|
   |`<command:inputTypes>`|Ajoute du contenu de la section d’entrées de la rubrique d’aide applet de commande. Pour plus d’informations, consultez [comment ajouter des Types d’entrée à une rubrique d’aide applet de commande](./how-to-add-input-types-to-a-cmdlet-help-topic.md).|
   |`<command:returnValues>`|Ajoute le contenu de la section des sorties de rubrique d’aide de l’applet de commande. Pour plus d’informations, consultez [comment ajouter la valeurs de retour pour une rubrique d’aide applet de commande](./how-to-add-return-values-to-a-cmdlet-help-topic.md).|
   |`<maml:alertset>`|Ajoute du contenu à la section Remarques de la rubrique d’aide de l’applet de commande. Pour plus d’informations, consultez [comment ajouter des Notes à une rubrique d’aide applet de commande](./how-to-add-notes-to-a-cmdlet-help-topic.md).|
   |`<command:examples>`|Ajoute le contenu de la section Exemples de la rubrique d’aide de l’applet de commande. Pour plus d’informations, consultez [comment ajouter des exemples pour une rubrique d’aide applet de commande](./how-to-add-examples-to-a-cmdlet-help-topic.md).|
   |`<maml:relatedLinks>`|Ajoute du contenu de la section liens connexes de rubrique d’aide de l’applet de commande. Pour plus d’informations, consultez [comment ajouter des liens connexes à une rubrique d’aide applet de commande](./how-to-add-related-links-to-a-cmdlet-help-topic.md).|

## <a name="example"></a>Exemple

 Voici un exemple d’un nœud de commande qui inclut les nœuds pour les différentes sections de la rubrique d’aide de l’applet de commande.

```xml
<command:command
  xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
  xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
  <command:details>
    <!--Add name an synopsis here-->
  </command:details>
  <maml:description>
    <!--Add detailed description here-->
  </maml:description>
  <command:syntax>
    <!--Add syntax information here-->
  </command:syntax>
  <command:parameters>
    <!--Add parameter information here-->
  </command:parameters>
  <command:inputTypes>
    <!--Add input type information here-->
  </command:inputTypes>
  <command:returnValues>
    <!--Add return value information here-->
  </command:returnValues>
  <maml:alertSet>
    <!--Add Note information here-->
  </maml:alertSet>
  <command:examples>
    <!--Add cmdlet examples here-->
  </command:examples>
  <maml:relatedLinks>
    <!--Add links to related content here-->
  </maml:relatedLinks>
</command:command>
```

## <a name="see-also"></a>Voir aussi

 [Comment ajouter le nom de l’applet de commande et le résumé](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [Comment ajouter la Description détaillée à une rubrique d’aide applet de commande](./how-to-add-a-cmdlet-description.md)

 [Comment ajouter la syntaxe pour une rubrique d’aide applet de commande](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Comment ajouter des paramètres à une rubrique d’aide applet de commande](./how-to-add-parameter-information.md)

 [Comment ajouter des Types d’entrée à une rubrique d’aide applet de commande](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Comment ajouter des valeurs de retour à une rubrique d’aide applet de commande](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Comment ajouter des Notes à une rubrique d’aide applet de commande](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Comment ajouter des exemples à une rubrique d’aide applet de commande](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Comment ajouter des liens connexes à une rubrique d’aide applet de commande](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)