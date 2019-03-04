---
title: Ajout de ressources à un Service Web OData de gestion | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e620bf6d-76be-47b0-a7a8-f43418f30c60
caps.latest.revision: 6
ms.openlocfilehash: b81a32b867795ae51c3f5308c2f82c31ed2747fa
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858365"
---
# <a name="adding-resources-to-a-management-odata-web-service"></a>Ajout de ressources à un service web Management OData

Cet exemple montre comment ajouter une ressource à un service web de gestion OData existant en utilisant le Concepteur de schémas de gestion OData. Le [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) exemple crée un service web qui expose les ressources de processus et le serveur. Dans cet exemple, vous allez ajouter une ressource de Machine virtuelle (VM) pour le service web.

## <a name="prerequisites"></a>Conditions préalables

Cette rubrique part du principe que vous avez téléchargé et installé le [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) exemple comme décrit dans [création d’un Service de Web Windows PowerShell](./creating-a-management-odata-web-service.md), et que vous avez téléchargé et installé le [Concepteur de schémas de OData de gestion](https://marketplace.visualstudio.com/items?itemName=jlisc0.ManagementODataSchemaDesigner). Cette rubrique suppose également que vous disposez du module PowerShell de Windows Hyper-V installé sur l’ordinateur où vous configurez le point de terminaison Odata de gestion.

## <a name="adding-vm-as-a-resource-to-the-web-service"></a>Ajout de machine virtuelle en tant que ressource au Service Web

La première étape consiste à importer le schéma du point de terminaison OData de gestion existant dans le Concepteur de schémas. La procédure suivante décrit comment procéder.

#### <a name="importing-an-existing-schema-into-the-schema-designer"></a>L’importation d’un schéma existant dans le Concepteur de schémas

1. Ouvrez le Concepteur de schémas de OData de gestion.

2. À partir de la **fichier** menu, sélectionnez **fichier** ; **Nouveau** ; **Fichier**. Le **nouveau fichier** boîte de dialogue apparaît.

3. Cliquez sur **gestion OData modèle**, puis cliquez sur **Open**.

4. Avec le bouton droit dans la fenêtre principale, puis cliquez sur **fichier de schéma** ; **Importation**. Le **Open** boîte de dialogue apparaît.

5. Accédez au dossier où vous configurez le service web de gestion OData pour le [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) exemple. Si vous avez utilisé le script Windows PowerShell fourni avec cet exemple pour configurer le point de terminaison sans modifier le script, ce dossier est **C:\inetpub\wwwroot\Modata**. Sélectionnez Schema.MOF, puis cliquez sur **Open**.

   À ce stade, ouvrez les fichiers Schema.MOF et le fichier Schema.xml dans un éditeur de texte et notez qu’ils contiennent des mappages pour les ressources de processus et de Service. Utilise le fichier Schema.MOF [Distributed Management Task Force](https://www.dmtf.org/) standard de (DTMF) MOF (Managed Object). Le fichier schema.xml utilise un schéma XML qui est décrit dans [schéma de mappage de la ressource](./resource-mapping-schema.md).

   La procédure suivante décrit comment importer les applets de commande Hyper-V vers le modèle de schéma.

#### <a name="importing-cmdlets-into-the-schema"></a>L’importation des applets de commande dans le schéma

1. Avec le bouton droit sur une zone vide de la fenêtre Concepteur du schéma, puis cliquez sur **applets de commande Import**. Le **Assistant Importation d’applet de commande** boîte de dialogue apparaît.

2. Assurez-vous que **ordinateur Local** est sélectionnée, puis cliquez sur **suivant**.

3. Assurez-vous qu’installé les Modules Windows PowerShell est sélectionné, puis sélectionnez Hyper-V à partir de la liste déroulante. Cliquez sur **suivant**. Cliquez sur **Suivant**.

4. Dans le **substantif de l’applet de commande** liste, sélectionnez **machine virtuelle**. Cliquez sur **Suivant**.

5. Pour cet exemple, nous liera uniquement les commandes Get et Delete avec les applets de commande. Effacer la **créer** et **mise à jour** cases à cocher et assurez-vous que le **obtenir** et **supprimer** cases à cocher sont vérifiées. Assurez-vous que le `Get-VM` applet de commande est sélectionnée pour **obtenir**et le `Remove-VM` applet de commande est sélectionnée pour **supprimer**.

6. Étant donné que les métadonnées pour les applets de commande de machine virtuelle ne spécifient pas un type de sortie, vous devez exécuter l’applet de commande pour spécifier le type de sortie. Sélectionnez **type de sortie fournissez** et cliquez sur **exécuter l’applet de commande**. Le **applet de commande exécuter** boîte de dialogue apparaît. Cliquez sur **exécuter**. Le **Type CLR** est alimentée avec les `VirtualMachine` type. Cliquez sur **OK**, puis cliquez sur **suivant**.

7. Par défaut, toutes les propriétés de l’objet VirtualMachine sont sélectionnés. Vous pouvez effacer toutes les propriétés que vous ne souhaitez pas en tant que partie des données retournées lorsque vous demandez cette ressource à partir du service web. Cliquez sur **Suivant**.

8. Vous devez sélectionner au moins une propriété à utiliser en tant que clé. Sélectionnez **nom** dans la liste, puis cliquez sur **suivant**.

9. La fenêtre suivante vous permet de mapper des propriétés de la ressource de gestion OData aux propriétés des applets de commande sous-jacente. L’Assistant mappe les propriétés avec des noms identiques par défaut. Par exemple, le `ComputerName` propriété de la ressource est mappée à la `ComputerName` propriété des applets de commande.  Cela vous permet de spécifier le `ComputerName` propriété dans une demande au service web et ont la valeur que vous spécifiez être passée à la `Get-VM` applet de commande. `Id` et `Name` sont également mappés par défaut.

   10. Cliquez sur **suivant**, puis cliquez sur **Terminer**.

       La ressource de machine virtuelle apparaît maintenant dans la fenêtre du Concepteur de schéma. Vous pouvez examiner les propriétés et les opérations associées à la ressource. Ensuite, vous allez exporter les fichiers de schéma mis à jour dans le répertoire virtuel pour le service web.

#### <a name="exporting-schema-files-from-the-schema-designer"></a>Exportation de fichiers de schéma depuis le Concepteur de schémas

1. Avec le bouton droit sur une zone vide de la fenêtre Concepteur du schéma, puis cliquez sur **fichier de schéma** ; **Exporter**. Le **Enregistrer sous** boîte de dialogue apparaît.

2. Accédez au répertoire même à partir de l’endroit où vous avez importé le fichier MOF. Nommez le fichier identique à celui du fichier MOF d’origine (*.Schema.MOF par défaut), puis cliquez sur **enregistrer**. Confirmez que vous souhaitez remplacer le fichier existant.

   Bien qu’il n’est pas défini explicitement dans le **Enregistrer sous** boîte de dialogue, il remplace le Schema.MOF et le fichier Schema.xml.

## <a name="next-steps"></a>Étapes suivantes

Vous accédez à la nouvelle ressource de machine virtuelle à partir du service web de gestion OData, vous devez mettre à jour le fichier RbacConfiguration.xml pour autoriser l’accès au module Hyper-V Windows PowerShell comme décrit dans [en fonction du rôle de configuration de l’autorisation](./configuring-role-based-authorization.md), et vous devrez également redémarrer le service web.