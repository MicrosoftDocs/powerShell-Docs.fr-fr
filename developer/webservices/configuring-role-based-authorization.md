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
# <a name="configuring-role-based-authorization"></a><span data-ttu-id="06b68-102">Configuration d’une autorisation en fonction du rôle</span><span class="sxs-lookup"><span data-stu-id="06b68-102">Configuring Role-based Authorization</span></span>

<span data-ttu-id="06b68-103">Cette rubrique montre comment configurer la stratégie d’autorisation en fonction du rôle pour l’exemple d’implémentation de la [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) interface décrite dans [personnalisé de mise en œuvre Autorisation pour l’Extension ISS Management OData](./implementing-custom-authorization-for-a-management-odata-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="06b68-103">This topic demonstrates how to configure the role-based authorization policy for the sample implementation of the [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) interface described in [Implementing Custom Authorization for Management OData IIS Extension](./implementing-custom-authorization-for-a-management-odata-web-service.md).</span></span>

<span data-ttu-id="06b68-104">Dans cet exemple, vous allez configurer un fichier XML qui est utilisé par l’exemple d’application IIS Management OData pour définir la stratégie d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="06b68-104">In this example, you will configure an XML file that is used by the sample Management OData application to define the authorization policy.</span></span> <span data-ttu-id="06b68-105">Vous créez deux rôles et associer différents modules de Windows PowerShell qui contiennent des flux de travail avec ces rôles.</span><span class="sxs-lookup"><span data-stu-id="06b68-105">You will create two roles and associate different Windows PowerShell modules that contain workflows with those roles.</span></span> <span data-ttu-id="06b68-106">Le schéma qui définit le fichier XML n’est répertorié à [en fonction du rôle de schéma de Configuration d’autorisation](./role-based-authorization-configuration-schema.md).</span><span class="sxs-lookup"><span data-stu-id="06b68-106">The schema that defines the XML file is listed at [Role-Based Authorization Configuration Schema](./role-based-authorization-configuration-schema.md).</span></span>

## <a name="modifying-the-rbacconfigurationxml-file"></a><span data-ttu-id="06b68-107">Modification du fichier RBacConfiguration.xml</span><span class="sxs-lookup"><span data-stu-id="06b68-107">Modifying the RBacConfiguration.xml File</span></span>

<span data-ttu-id="06b68-108">Ce fichier définit la stratégie d’autorisation pour l’application.</span><span class="sxs-lookup"><span data-stu-id="06b68-108">This file defines the authorization policy for the application.</span></span> <span data-ttu-id="06b68-109">Les rôles sont définis à l’aide de `Group` nœuds.</span><span class="sxs-lookup"><span data-stu-id="06b68-109">Roles are defined by using `Group` nodes.</span></span> <span data-ttu-id="06b68-110">Un `Group` nœud définit les commandes Windows PowerShell que les utilisateurs affectés à ce groupe peuvent exécuter.</span><span class="sxs-lookup"><span data-stu-id="06b68-110">A `Group` node defines the Windows PowerShell commands that users assigned to that group can run.</span></span> <span data-ttu-id="06b68-111">Les utilisateurs sont affectés à des groupes à l’aide de `User` nœuds.</span><span class="sxs-lookup"><span data-stu-id="06b68-111">Users are assigned to groups by using `User` nodes.</span></span>

<span data-ttu-id="06b68-112">Dans ces exemples, vous allez ajouter un module à l’administrateur `Group` nœud, et ajouter un utilisateur à chaque groupe.</span><span class="sxs-lookup"><span data-stu-id="06b68-112">In these examples, you will add a module to the Administrator `Group` node, and add a user to each group.</span></span>

#### <a name="adding-a-module-to-a-group-node"></a><span data-ttu-id="06b68-113">Ajout d’un Module à un nœud de groupe</span><span class="sxs-lookup"><span data-stu-id="06b68-113">Adding a Module to a Group Node</span></span>

1. <span data-ttu-id="06b68-114">Créez un fichier nommé **RBacConfiguration.xml** dans un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="06b68-114">Create a file named **RBacConfiguration.xml** in a text editor.</span></span> <span data-ttu-id="06b68-115">Ce fichier doit être enregistré dans le répertoire de l’application principale pour votre service web.</span><span class="sxs-lookup"><span data-stu-id="06b68-115">This file should be saved to the main application directory for your web service.</span></span> <span data-ttu-id="06b68-116">Insérer le texte suivant dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="06b68-116">Insert the following text in the file.</span></span>

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

2. <span data-ttu-id="06b68-117">Le fichier contient deux `Group` nœuds.</span><span class="sxs-lookup"><span data-stu-id="06b68-117">The file contains two `Group` nodes.</span></span> <span data-ttu-id="06b68-118">Ils représentent les deux rôles utilisés dans cet exemple, le `NonAdminGroup` et `AdminGroup` rôles.</span><span class="sxs-lookup"><span data-stu-id="06b68-118">These represent the two roles used in this example, the `NonAdminGroup` and the `AdminGroup` roles.</span></span>

   <span data-ttu-id="06b68-119">Directement après la fermeture `Cmdlets` balise dans la première `Group` nœud, ajoutez le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="06b68-119">Directly after the closing `Cmdlets` tag in the first `Group` node, add the following XML:</span></span>

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a><span data-ttu-id="06b68-120">Ajout d’un utilisateur à un nœud de groupe</span><span class="sxs-lookup"><span data-stu-id="06b68-120">Adding a User to a Group Node</span></span>

1. <span data-ttu-id="06b68-121">Ouvrez le **RBacConfiguration.xml** fichier dans un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="06b68-121">Open the **RBacConfiguration.xml** file in a text editor.</span></span> <span data-ttu-id="06b68-122">Ce fichier se trouve dans le dossier C:\\\inetpub\wwwroot\Modata si vous n’avez pas modifié le nom de point de terminaison avant l’installation.</span><span class="sxs-lookup"><span data-stu-id="06b68-122">This file is located in the folder C:\\\inetpub\wwwroot\Modata  if you did not change the endpoint name before installation.</span></span>

2. <span data-ttu-id="06b68-123">Directement après la balise de fermeture dans le `Users` nœud, ajoutez le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="06b68-123">Directly after the closing tag in the `Users` node, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. <span data-ttu-id="06b68-124">Directement après que le code XML ajouté à l’étape précédente, ajoutez le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="06b68-124">Directly after the XML added in the previous step, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```