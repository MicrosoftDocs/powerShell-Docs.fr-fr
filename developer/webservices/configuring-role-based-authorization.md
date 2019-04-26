---
title: Configuration des autorisations en fonction du rôle | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2933a6ca-fe92-4ba2-97ee-ef0f0d5fdfcf
caps.latest.revision: 8
ms.openlocfilehash: b73284adb4bf228510bf8134aa4c6a10561b7ea2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080677"
---
# <a name="configuring-role-based-authorization"></a>Configuration d’une autorisation en fonction du rôle

Cette rubrique montre comment configurer la stratégie d’autorisation en fonction du rôle pour l’exemple d’implémentation de la [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) interface décrite dans [personnalisé de mise en œuvre Autorisation pour l’Extension ISS Management OData](./implementing-custom-authorization-for-a-management-odata-web-service.md).

Dans cet exemple, vous allez configurer un fichier XML qui est utilisé par l’exemple d’application IIS Management OData pour définir la stratégie d’autorisation. Vous créez deux rôles et associer différents modules de Windows PowerShell qui contiennent des flux de travail avec ces rôles. Le schéma qui définit le fichier XML n’est répertorié à [en fonction du rôle de schéma de Configuration d’autorisation](./role-based-authorization-configuration-schema.md).

## <a name="modifying-the-rbacconfigurationxml-file"></a>Modification du fichier RBacConfiguration.xml

Ce fichier définit la stratégie d’autorisation pour l’application. Les rôles sont définis à l’aide de `Group` nœuds. Un `Group` nœud définit les commandes Windows PowerShell que les utilisateurs affectés à ce groupe peuvent exécuter. Les utilisateurs sont affectés à des groupes à l’aide de `User` nœuds.

Dans ces exemples, vous allez ajouter un module à l’administrateur `Group` nœud, et ajouter un utilisateur à chaque groupe.

#### <a name="adding-a-module-to-a-group-node"></a>Ajout d’un Module à un nœud de groupe

1. Créez un fichier nommé **RBacConfiguration.xml** dans un éditeur de texte. Ce fichier doit être enregistré dans le répertoire de l’application principale pour votre service web. Insérer le texte suivant dans le fichier.

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

2. Le fichier contient deux `Group` nœuds. Ils représentent les deux rôles utilisés dans cet exemple, le `NonAdminGroup` et `AdminGroup` rôles.

   Directement après la fermeture `Cmdlets` balise dans la première `Group` nœud, ajoutez le code XML suivant :

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a>Ajout d’un utilisateur à un nœud de groupe

1. Ouvrez le **RBacConfiguration.xml** fichier dans un éditeur de texte. Ce fichier se trouve dans le dossier C:\\\inetpub\wwwroot\Modata si vous n’avez pas modifié le nom de point de terminaison avant l’installation.

2. Directement après la balise de fermeture dans le `Users` nœud, ajoutez le code XML suivant :

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. Directement après que le code XML ajouté à l’étape précédente, ajoutez le code XML suivant :

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```