---
title: Configuration de l’autorisation basée sur les rôles | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2933a6ca-fe92-4ba2-97ee-ef0f0d5fdfcf
caps.latest.revision: 8
ms.openlocfilehash: 2c9d6040b7a9c17dc5204c8eb835fd69780f62c5
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564255"
---
# <a name="configuring-role-based-authorization"></a>Configuration d’une autorisation en fonction du rôle

Cette rubrique montre comment configurer la stratégie d’autorisation basée sur les rôles pour l’implémentation de l’exemple de l’interface [Microsoft. Management. OData. Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) décrite dans [implémentation d’une autorisation personnalisée pour l’extension IIS de gestion OData](./implementing-custom-authorization-for-a-management-odata-web-service.md).

Dans cet exemple, vous allez configurer un fichier XML utilisé par l’exemple d’application de gestion OData pour définir la stratégie d’autorisation. Vous allez créer deux rôles et associer différents modules Windows PowerShell qui contiennent des flux de travail à ces rôles. Le schéma qui définit le fichier XML est indiqué dans [schéma de configuration de l’autorisation basée sur les rôles](./role-based-authorization-configuration-schema.md).

## <a name="modifying-the-rbacconfigurationxml-file"></a>Modification du fichier RBacConfiguration. Xml

Ce fichier définit la stratégie d’autorisation pour l’application. Les rôles sont définis à l’aide de `Group` nœuds. Un `Group` nœud définit les commandes Windows PowerShell que les utilisateurs affectés à ce groupe peuvent exécuter. Les utilisateurs sont affectés à des groupes à l’aide de `User` nœuds.

Dans ces exemples, vous allez ajouter un module au nœud administrateur `Group` et ajouter un utilisateur à chaque groupe.

#### <a name="adding-a-module-to-a-group-node"></a>Ajout d’un module à un nœud de groupe

1. Créez un fichier nommé **RBacConfiguration. xml** dans un éditeur de texte. Ce fichier doit être enregistré dans le répertoire principal de l’application pour votre service Web. Insérez le texte suivant dans le fichier.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <RbacConfiguration>
     <Groups>
       <!--Group consists of the following:
         Name:  Name of the group
         UserName (Optional): Windows Identity user name
         Password (Optional): Password of the Windows user name
         DomainName (Optional): Domain for the user. For local machine account either do not include them or give the machine name. Do not give empty string
         MapIncomingUser (Optional): Boolean value indicating whether to execute cmdlet in the context of network client.

         User credentials and MapIncomingUser=true are exclusive.
       -->
       <Group Name="NonAdminGroup" MapIncomingUser="true">
         <Cmdlets>
           <Cmdlet>Get-Service</Cmdlet>
           <Cmdlet>Set-Service</Cmdlet>
           <Cmdlet>Get-Process</Cmdlet>
           <Cmdlet>Get-Item</Cmdlet>
           <Cmdlet>New-Item</Cmdlet>
           <Cmdlet>Get-Command</Cmdlet>
           <Cmdlet>ConvertTo-Xml</Cmdlet>
           <Cmdlet>ConvertTo-Json</Cmdlet>
           <Cmdlet>ConvertFrom-Json</Cmdlet>
         </Cmdlets>
       </Group>
       <Group Name="AdminGroup" MapIncomingUser="true">
         <Cmdlets>
           <Cmdlet>Get-Service</Cmdlet>
           <Cmdlet>Get-Process</Cmdlet>
           <Cmdlet>Get-Item</Cmdlet>
           <Cmdlet>New-Item</Cmdlet>
           <Cmdlet>Get-Command</Cmdlet>
           <Cmdlet>ConvertTo-Xml</Cmdlet>
           <Cmdlet>ConvertTo-Json</Cmdlet>
           <Cmdlet>ConvertFrom-Json</Cmdlet>
         </Cmdlets>
         <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
       </Group>
     </Groups>
     <Users>
       <!-- User consists of the following :
         Name: Name of the user. If a user is from a cer
         AuthenticationType: Authentication type used.
         DomainName (Optional): Domain for the user
       -->
       <User Name="localNonAdmin" AuthenticationType="Basic" GroupName="NonAdminGroup" />
       <User Name="localAdmin" AuthenticationType="Basic" GroupName="AdminGroup" />
     </Users>
   </RbacConfiguration>
   ```

2. Le fichier contient deux `Group` nœuds. Celles-ci représentent les deux rôles utilisés dans cet exemple, les `NonAdminGroup` `AdminGroup` rôles et.

   Juste après la `Cmdlets` balise de fermeture dans le premier `Group` nœud, ajoutez le code XML suivant :

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a>Ajout d’un utilisateur à un nœud de groupe

1. Ouvrez le fichier **RBacConfiguration. xml** dans un éditeur de texte. Ce fichier se trouve dans le dossier C : \\ \inetpub\wwwroot\Modata si vous n’avez pas modifié le nom du point de terminaison avant l’installation.

2. Juste après la balise de fermeture dans le `Users` nœud, ajoutez le code XML suivant :

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. Juste après le XML ajouté à l’étape précédente, ajoutez le code XML suivant :

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```
