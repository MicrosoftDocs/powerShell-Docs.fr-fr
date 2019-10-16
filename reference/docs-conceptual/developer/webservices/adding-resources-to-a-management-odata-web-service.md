---
title: Ajout de ressources à un service Web OData de gestion | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e620bf6d-76be-47b0-a7a8-f43418f30c60
caps.latest.revision: 6
ms.openlocfilehash: b81a32b867795ae51c3f5308c2f82c31ed2747fa
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359818"
---
# <a name="adding-resources-to-a-management-odata-web-service"></a>Ajout de ressources à un service web Management OData

Cet exemple montre comment ajouter une ressource à un service Web OData de gestion existant à l’aide du concepteur de schémas OData de gestion. L’exemple [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) crée un service Web qui expose les ressources de processus et de serveur. Dans cet exemple, vous allez ajouter une ressource de machine virtuelle (VM) au service Web.

## <a name="prerequisites"></a>Conditions préalables

Cette rubrique part du principe que vous avez téléchargé et installé l’exemple [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) comme décrit dans [création d’un service Web Windows PowerShell](./creating-a-management-odata-web-service.md)et que vous avez téléchargé et installé le [Concepteur de schémas OData Management](https://marketplace.visualstudio.com/items?itemName=jlisc0.ManagementODataSchemaDesigner). Cette rubrique suppose également que le module Windows PowerShell Hyper-V est installé sur l’ordinateur sur lequel vous avez configuré le point de terminaison OData de gestion.

## <a name="adding-vm-as-a-resource-to-the-web-service"></a>Ajout d’une machine virtuelle en tant que ressource au service Web

La première étape consiste à importer le schéma à partir du point de terminaison de gestion OData existant dans le concepteur de schémas. La procédure suivante décrit comment procéder.

#### <a name="importing-an-existing-schema-into-the-schema-designer"></a>Importation d’un schéma existant dans le concepteur de schémas

1. Ouvrez le concepteur de schémas OData de gestion.

2. Dans le menu **fichier** , sélectionnez **fichier** ; **Nouveau** ; **Fichier**. La boîte **de dialogue nouveau fichier** s’affiche.

3. Cliquez sur **gestion OData Model**, puis sur **ouvrir**.

4. Cliquez avec le bouton droit dans la fenêtre principale, puis cliquez sur **fichier de schéma** . **Importation**. La boîte de dialogue **ouvrir** s’affiche.

5. Accédez au dossier dans lequel vous configurez le service Web OData de gestion pour l’exemple [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) . Si vous avez utilisé le script Windows PowerShell fourni avec cet exemple pour configurer le point de terminaison sans modifier le script, ce dossier est **C:\inetpub\wwwroot\Modata**. Sélectionnez Schema. mof, puis cliquez sur **ouvrir**.

   À ce stade, ouvrez les fichiers Schema. mof et Schema. xml dans un éditeur de texte, et Notez qu’ils contiennent des mappages pour les ressources de processus et de service. Le fichier Schema. mof utilise la norme MOF ( [Distributed Management Task Force](https://www.dmtf.org/) ). Le fichier Schema. xml utilise un schéma XML qui est décrit dans [schéma de mappage des ressources](./resource-mapping-schema.md).

   La procédure suivante décrit comment importer des applets de commande Hyper-V dans le modèle de schéma.

#### <a name="importing-cmdlets-into-the-schema"></a>Importation des applets de commande dans le schéma

1. Cliquez avec le bouton droit sur une zone vide de la fenêtre du concepteur de schémas, puis cliquez sur **importer des applets**de commande. La boîte de dialogue **Assistant importation d’applet** de commande s’affiche.

2. Assurez-vous que l’option **ordinateur local** est sélectionnée, puis cliquez sur **suivant**.

3. Assurez-vous que l’option modules Windows PowerShell installés est sélectionnée, puis sélectionnez Hyper-V dans la liste déroulante. Cliquez sur **suivant**. Cliquez sur **Suivant**.

4. Dans la liste nom de l' **applet** de commande, sélectionnez **VM**. Cliquez sur **Suivant**.

5. Pour cet exemple, nous allons lier uniquement les commandes obtenir et supprimer avec des applets de commande. Désactivez les cases à cocher **créer** et **mettre à jour** , et assurez-vous que les cases à cocher **récupérer** et **supprimer** sont activées. Assurez-vous que l’applet de commande `Get-VM` est sélectionnée pour **obtenir**et que l’applet de commande `Remove-VM` est sélectionnée pour la **suppression**.

6. Étant donné que les métadonnées des applets de commande de machine virtuelle ne spécifient pas de type de sortie, vous devez exécuter l’applet de commande pour spécifier le type de sortie. Sélectionnez **fournir le type de sortie** , puis cliquez sur **exécuter l’applet de commande**. La boîte de dialogue **exécuter l’applet de commande** s’affiche. Cliquez sur **exécuter**. La zone de **type CLR** est remplie avec le type `VirtualMachine`. Cliquez sur **OK**, puis sur **suivant**.

7. Par défaut, toutes les propriétés de l’objet VirtualMachine sont sélectionnées. Vous pouvez effacer toutes les propriétés que vous ne souhaitez pas inclure dans les données retournées lorsque vous demandez cette ressource à partir du service Web. Cliquez sur **Suivant**.

8. Vous devez sélectionner au moins une propriété à utiliser comme clé. Sélectionnez **nom** dans la liste, puis cliquez sur **suivant**.

9. La fenêtre suivante vous permet de mapper les propriétés de la ressource OData de gestion aux propriétés des applets de commande sous-jacentes. L’Assistant mappe les propriétés avec des noms identiques par défaut. Par exemple, la propriété `ComputerName` de la ressource est mappée à la propriété `ComputerName` des applets de commande.  Cela vous permet de spécifier la propriété `ComputerName` dans une demande adressée au service Web et de faire en sorte que la valeur que vous spécifiez soit transmise à l’applet de commande `Get-VM`. `Id` et `Name` sont également mappés par défaut.

   10. Cliquez sur **suivant**, puis sur **Terminer**.

       La ressource de machine virtuelle s’affiche maintenant dans la fenêtre du concepteur de schémas. Vous pouvez examiner les propriétés et les opérations associées à la ressource. Ensuite, vous allez exporter les fichiers de schéma mis à jour dans le répertoire virtuel pour le service Web.

#### <a name="exporting-schema-files-from-the-schema-designer"></a>Exportation de fichiers de schéma à partir du concepteur de schémas

1. Cliquez avec le bouton droit sur une zone vide de la fenêtre du concepteur de schémas, puis cliquez sur **fichier de schéma** . **Exportation**. La boîte de dialogue **Enregistrer sous** s’affiche.

2. Accédez au même répertoire que celui à partir duquel vous avez importé le fichier MOF. Nommez le fichier de la même façon que le fichier MOF d’origine (Schema. mof par défaut), puis cliquez sur **Enregistrer**. Confirmez que vous souhaitez remplacer le fichier existant.

   Bien qu’elle ne soit pas explicitement indiquée dans la boîte de dialogue **Enregistrer sous** , les fichiers Schema. mof et Schema. XML sont remplacés.

## <a name="next-steps"></a>Étapes suivantes

Avant d’accéder à la nouvelle ressource de machine virtuelle à partir du service Web OData de gestion, vous devez mettre à jour le fichier RbacConfiguration. xml pour autoriser l’accès au module Windows PowerShell Hyper-V, comme décrit dans Configuration de l' [autorisation basée sur les rôles](./configuring-role-based-authorization.md), et vous pouvez également vous devez redémarrer le service Web.