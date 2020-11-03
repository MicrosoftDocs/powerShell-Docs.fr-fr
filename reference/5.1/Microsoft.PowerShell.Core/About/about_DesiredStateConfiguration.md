---
description: Fournit une brève introduction à la fonctionnalité de configuration d’état souhaité (DSC) PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_desiredstateconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_DesiredStateConfiguration
ms.openlocfilehash: 2f043104c67078b98355b3e54171a8993e534837
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208730"
---
# <a name="about_desiredstateconfiguration"></a>about_DesiredStateConfiguration

## <a name="short-description"></a>DESCRIPTION COURTE

Fournit une brève introduction à la fonctionnalité de configuration d’état souhaité (DSC) PowerShell.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

DSC est une plateforme de gestion dans PowerShell qui permet de déployer et de gérer les données de configuration des services logiciels, et de gérer l’environnement dans lequel ces services s’exécutent.

DSC fournit un ensemble d’extensions de langage PowerShell, de nouvelles applets de commande et de ressources que vous pouvez utiliser pour spécifier de façon déclarative la manière dont vous souhaitez que l’état de votre environnement logiciel soit configuré. DSC vous permet également de mettre à jour et de gérer des configurations existantes.

DSC est introduit dans PowerShell 4,0.

Pour plus d’informations sur DSC, consultez [vue d’ensemble de la configuration de l’état souhaité PowerShell](/powershell/scripting/dsc/overview/overview) dans la bibliothèque TechNet.

## <a name="developing-dsc-resources-with-classes"></a>DÉVELOPPEMENT DE RESSOURCES DSC AVEC DES CLASSES

À compter de PowerShell 5,0, vous pouvez développer des ressources DSC à l’aide de classes.
Pour plus d’informations, consultez [about_Classes](about_Classes.md)et [écriture d’une ressource DSC personnalisée avec les classes PowerShell](/previous-versions//dn948461(v=technet.10)) sur Microsoft TechNet.

## <a name="using-dsc"></a>UTILISATION DE DSC

Pour utiliser DSC pour configurer votre environnement, commencez par définir un bloc de script PowerShell à l’aide du mot clé configuration, suivi d’un identificateur, qui est à son tour suivi de la paire d’accolades délimitant le bloc. Dans le bloc de configuration, vous pouvez définir des blocs de nœuds qui spécifient l’état de configuration souhaité pour chaque nœud (ordinateur) de l’environnement. Un bloc node commence par le mot clé node, suivi du nom de l’ordinateur cible, qui peut être une variable. Après le nom de l’ordinateur, placez les accolades qui délimitent le bloc de nœud. À l’intérieur du bloc node, vous pouvez définir des blocs de ressources pour configurer des ressources spécifiques. Un bloc de ressources commence par le nom de type de la ressource, suivi de l’identificateur que vous souhaitez spécifier pour ce bloc, suivi des accolades qui délimitent le bloc, comme illustré dans l’exemple suivant.

```powershell
Configuration MyWebConfig {
    # Parameters are optional
    param ($MachineName, $WebsiteFilePath)
    # A Configuration block can have one or more Node blocks
    Node $MachineName
    {
        # Next, specify one or more resource blocks
        # WindowsFeature is one of the resources you can use in a Node block
        # This example ensures the Web Server (IIS) role is installed
        WindowsFeature IIS
        {
            # To ensure that the role is not installed, set Ensure to "Absent"
            Ensure = "Present"
            Name = "Web-Server" # Use the Name property from Get-WindowsFeature
        }

        # You can use the File resource to create files and folders
        # "WebDirectory" is the name you want to use to refer to this instance
        File WebDirectory
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File"
            Recurse = $true
            SourcePath = $WebsiteFilePath
            DestinationPath = "C:\inetpub\wwwroot"

            # Ensure that the IIS block is successfully run first before
            # configuring this resource
            DependsOn = "[WindowsFeature]IIS"  # Use for dependencies
        }
    }
}
```

Pour créer une configuration, appelez le bloc de configuration de la même façon que vous appelez une fonction PowerShell, en transmettant tous les paramètres attendus que vous avez définis (deux dans l’exemple ci-dessus). Par exemple, dans ce cas :

```powershell
MyWebConfig -MachineName "TestMachine" -WebsiteFilePath `
  "\\filesrv\WebFiles" -OutputPath "C:\Windows\system32\temp"
# OutputPath is optional
```

Cela génère un fichier MOF par nœud dans le chemin d’accès que vous spécifiez. Ces fichiers MOF spécifient la configuration souhaitée pour chaque nœud. Ensuite, utilisez l’applet de commande suivante pour analyser les fichiers MOF de configuration, envoyer la configuration correspondante à chaque nœud et appliquer ces configurations. Notez que vous n’avez pas besoin de créer un fichier MOF distinct pour les ressources DSC basées sur une classe.

```powershell
Start-DscConfiguration -Verbose -Wait -Path "C:\Windows\system32\temp"
```

## <a name="using-dsc-to-maintain-configuration-state"></a>UTILISATION DE DSC POUR MAINTENIR L’ÉTAT DE CONFIGURATION

Avec DSC, la configuration est idempotent. Cela signifie que si vous utilisez DSC pour mettre en œuvre la même configuration plusieurs fois, l’état de configuration qui en résulte sera toujours le même. Pour cette raison, si vous pensez que tous les nœuds de votre environnement peuvent avoir été dérives de l’état souhaité de la configuration, vous pouvez réactiver la même configuration DSC pour rétablir l’état souhaité. Vous n’avez pas besoin de modifier le script de configuration pour ne traiter que les ressources dont l’État est dérivé de l’état souhaité.

L’exemple suivant montre comment vérifier si l’état réel de la configuration sur un nœud donné est dérivé de la dernière configuration DSC sur le nœud. Dans cet exemple, nous vérifions la configuration de l’ordinateur local.

```powershell
$session = New-CimSession -ComputerName "localhost"
Test-DscConfiguration -CimSession $session
```

## <a name="built-in-dsc-resources"></a>RESSOURCES DSC INTÉGRÉES

Vous pouvez utiliser les ressources intégrées suivantes dans vos scripts de configuration :

|Nom                  |Propriétés                                         |
|----------------------|---------------------------------------------------|
|Fichier                  |{DestinationPath, attributs, Checksum, contenu...}|
|Archivage               |{Destination, chemin d’accès, somme de contrôle, informations d’identification...}       |
|Environnement           |{Nom, DependsOn, vérifier, chemin d’accès...}                 |
|Groupe                 |{GroupName, Credential, DependsOn, Description...} |
|Journal                   |{Message, DependsOn, PsDscRunAsCredential}         |
|Paquet               |{Nom, chemin d’accès, ProductId, arguments...}              |
|Registre              |{Key, ValueName, DependsOn, vérifiez...}             |
|Script                |{GetScript, Setscript s’exécute, TestScript, Credential...}  |
|Service               |{Nom, BuiltInAccount, informations d’identification, dépendances...}|
|Utilisateur                  |{UserName, DependsOn, description, Disabled...}    |
|WaitForAll            |{NodeName, ResourceName, DependsOn, PsDscRunAsC...}|
|WaitForAny            |{NodeName, ResourceName, DependsOn, PsDscRunAsC...}|
|WaitForSome           |{NodeCount, NodeName, ResourceName, DependsOn...}  |
|WindowsFeature        |{Nom, informations d’identification, DependsOn, vérifier...}           |
|WindowsOptionalFeature|{Nom, DependsOn, vérifier, LogLevel...}             |
|WindowsProcess        |{Arguments, chemin d’accès, informations d’identification, DependsOn...}        |

Pour obtenir la liste des ressources DSC disponibles sur votre système, exécutez l' `Get-DscResource` applet de commande.

> [!NOTE]
> Dans les versions de PowerShell inférieures à 7.0, `Get-DscResource` ne trouve pas les ressources DSC basées sur une classe.

L’exemple de cette rubrique montre comment utiliser les ressources file et WindowsFeature. Pour afficher toutes les propriétés que vous pouvez utiliser avec une ressource, insérez le curseur dans le mot clé de ressource (par exemple, fichier) dans votre script de configuration dans PowerShell ISE, maintenez la <kbd>touche Ctrl</kbd> + <kbd>espace</kbd> enfoncée.

## <a name="find-more-resources"></a>RECHERCHER D’AUTRES RESSOURCES

Vous pouvez télécharger, installer et découvrir de nombreuses autres ressources DSC disponibles qui ont été créées par la communauté d’utilisateurs PowerShell et DSC, et par Microsoft. Visitez le [PowerShell Gallery](https://www.powershellgallery.com/) pour parcourir les ressources DSC disponibles et en savoir plus.

## <a name="see-also"></a>VOIR AUSSI

[Vue d’ensemble de la configuration d’état souhaité PowerShell](/powershell/scripting/dsc/overview/overview)

[Ressources de configuration d’état souhaité PowerShell intégrées](/powershell/scripting/dsc/resources/resources)

[Créer des ressources de configuration d’état souhaité PowerShell personnalisées](/powershell/scripting/dsc/resources/authoringResource)
