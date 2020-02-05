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
ms.openlocfilehash: 186a8ceecea47564503dc181a76cc314033b6d3f
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76996035"
---
# <a name="how-to-create-the-cmdlet-help-file"></a>Guide pratique pour créer le fichier d’aide d’une applet de commande

Cette section décrit comment créer un fichier XML valide contenant du contenu pour les rubriques d’aide sur les applets de commande Windows PowerShell. Cette section explique comment nommer le fichier d’aide, comment ajouter les en-têtes XML appropriés et comment ajouter des nœuds qui contiendront les différentes sections du contenu d’aide de l’applet de commande.

> [!NOTE]
> Pour obtenir une vue complète d’un fichier d’aide, ouvrez l’un des fichiers dll-Help. XML qui se trouvent dans le répertoire d’installation de Windows PowerShell. Par exemple, le fichier Microsoft. PowerShell. Commands. Management. dll-Help. xml contient du contenu pour plusieurs des applets de commande Windows PowerShell.

### <a name="how-to-create-a-cmdlet-help-file"></a>Comment créer un fichier d’aide d’applet de commande

1. Créez un fichier texte et enregistrez-le à l’aide de l’encodage UTF8. Le nom de fichier doit avoir le format suivant afin que Windows PowerShell puisse le détecter en tant que fichier d’aide de l’applet de commande.

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. Ajoutez les en-têtes XML suivants au fichier texte. Sachez que le fichier sera validé par rapport au schéma MAML (multi-agent Modeling Language). Actuellement, Windows PowerShell ne fournit aucun outil pour valider le fichier.

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. Ajoutez un nœud de commande au fichier d’aide de l’applet de commande pour chaque applet de commande dans l’assembly. Chaque nœud du nœud de commande est associé aux différentes sections de la rubrique d’aide de l’applet de commande.

   Le tableau suivant répertorie l’élément XML pour chaque nœud, suivi d’une description de chaque nœud.

   |Nœud|Description|
   |----------|-----------------|
   |`<details>`|Ajoute du contenu pour les sections nom et SYNOPSIS de la rubrique d’aide de l’applet de commande. Pour plus d’informations, consultez [comment ajouter le nom de l’applet de commande et le synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).|
   |`<maml:description>`|Ajoute du contenu pour la section DESCRIPTION de la rubrique d’aide de l’applet de commande. Pour plus d’informations, consultez [comment ajouter la description détaillée à une rubrique d’aide sur une applet](./how-to-add-a-cmdlet-description.md)de commande.|
   |`<command:syntax>`|Ajoute du contenu pour la section syntaxe de la rubrique d’aide de l’applet de commande. Pour plus d’informations, consultez [comment ajouter une syntaxe à une rubrique d’aide sur une applet](./how-to-add-syntax-to-a-cmdlet-help-topic.md)de commande.|
   |`<command:parameters>`|Ajoute du contenu pour la section paramètres de la rubrique d’aide de l’applet de commande. Pour plus d’informations, consultez [comment ajouter des paramètres à une rubrique d’aide sur une applet](./how-to-add-parameter-information.md)de commande.|
   |`<command:inputTypes>`|Ajoute du contenu pour la section des entrées de la rubrique d’aide de l’applet de commande. Pour plus d’informations, consultez [comment ajouter des types d’entrée à une rubrique d’aide sur une applet](./how-to-add-input-types-to-a-cmdlet-help-topic.md)de commande.|
   |`<command:returnValues>`|Ajoute du contenu pour la section sorties de la rubrique d’aide de l’applet de commande. Pour plus d’informations, consultez [comment ajouter des valeurs de retour à une rubrique d’aide sur une applet](./how-to-add-return-values-to-a-cmdlet-help-topic.md)de commande.|
   |`<maml:alertset>`|Ajoute du contenu à la section Remarques de la rubrique d’aide de l’applet de commande. Pour plus d’informations, consultez [comment ajouter des notes à une rubrique d’aide sur une applet](./how-to-add-notes-to-a-cmdlet-help-topic.md)de commande.|
   |`<command:examples>`|Ajoute du contenu pour la section Exemples de la rubrique d’aide de l’applet de commande. Pour plus d’informations, consultez [comment ajouter des exemples à une rubrique d’aide sur une applet](./how-to-add-examples-to-a-cmdlet-help-topic.md)de commande.|
   |`<maml:relatedLinks>`|Ajoute du contenu pour la section Liens connexes de la rubrique d’aide de l’applet de commande. Pour plus d’informations, consultez [comment ajouter des liens connexes à une rubrique d’aide sur une applet](./how-to-add-related-links-to-a-cmdlet-help-topic.md)de commande.|

## <a name="example"></a>Exemple

 Voici un exemple de nœud de commande qui comprend les nœuds des différentes sections de la rubrique d’aide de l’applet de commande.

```xml
<command:command
  xmlns:maml="https://schemas.microsoft.com/maml/2004/10"
  xmlns:command="https://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="https://schemas.microsoft.com/maml/dev/2004/10">
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

 [Comment ajouter le nom de l’applet de commande et le synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [Comment ajouter la description détaillée à une rubrique d’aide sur une applet de commande](./how-to-add-a-cmdlet-description.md)

 [Guide pratique pour ajouter une syntaxe à une rubrique d’aide sur une applet de commande](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Comment ajouter des paramètres à une rubrique d’aide sur une applet de commande](./how-to-add-parameter-information.md)

 [Comment ajouter des types d’entrée à une rubrique d’aide sur une applet de commande](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Comment ajouter des valeurs de retour à une rubrique d’aide sur une applet de commande](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Comment ajouter des notes à une rubrique d’aide sur une applet de commande](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Comment ajouter des exemples à une rubrique d’aide sur une applet de commande](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Comment ajouter des liens connexes à une rubrique d’aide sur une applet de commande](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)